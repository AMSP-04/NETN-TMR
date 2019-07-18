# NETN-TMR

Copyright (C) 2019 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENSE.md).

## Introduction

The type of control of entities in a federation can be of two kinds, entity control and attribute modelling responsibility. A federate with entity control, controls the actions and behaviour of simulated entities. A federate with attribute modelling responsibility, updates a set of attributes at simulated entities. 

### Purpose

The NETN-TMR FOM module is used to transfer attribute modelling responsibility between federates. A transfer is perfomed to dynamically change responsibility to a more suitable federate.

For example: 
- Transfer from a Live to a Virtual or Constructive simulation
- Transfer between Virtual and Constructive simulations
- Transfer between hi- and low-fidelity models
- Transfer to allow backup, maintenance or load-balancing
- Transfer of certain attributes to functional models such as movement, damage assessment etc.


### Scope

The transfer of ownership can be triggered either from an external source or by the requesting federate. The pattern has methods both for acquiring and divesting of instance attribute ownership. There is a correlation between TMR interactions and HLA Ownership services to ensure that the expected federates are involved in the transfer.

## Overview

### TMR Interactions and HLA Services
The TMR pattern defines five TMR interactions:
a.	Initiate;
b.	Request;
c.	Offer;
d.	Cancel Request; and
e.	Transfer Result.

The TMR pattern incorporates four RTIambassador HLA Ownership Management services:
a.	Attribute Ownership Acquisition (when negotiation);
b.	Attribute Ownership Acquisition If Available (without negotiation);
c.	Attribute Ownership Divesture If Wanted; and
d.	Cancel Attribute Ownership Acquisition.

The TMR pattern incorporates four FederateAmbassador (callbacks) HLA Ownership Management services:
a.	Request Attribute Ownership Release †;
b.	Attribute Ownership Acquisition Notification †;
c.	Confirm Attribute Ownership Acquisition Cancellation †; and
d.	Attribute OwnershipUnavailable †.
 
Figure 5-1: The Interaction Classes in TMR FOM Module.

## TMR PATTERN USAGE

### TMR Pattern Rules
1.	Before divesting instance attributes, the attributes shall be updated (HLA service Update Attribute Values).
2.	After acquisition of instance attributes, the attributes shall be updated (HLA service Update Attribute Values).

### Transfer Type
The type of the transfer can be Acquire, Divest or AcquireWithoutNegotiating. The requesting federate specifies the transfer type or if the transfer process is triggered from outside, the initiating interaction specifies the transfer type.

### TMR Interactions

#### Interaction: TMR
1.	The super interaction, containing parameters for use in its specializations.
Parameter: TMR.TransactionID
2.	A structure with two fields, Counter and Federate Handle. The Transaction ID should, where possible, be encoded and used as the User Supplied Tag in the HLA Ownership services to get a correlation between the TMR interactions and HLA Ownership services.
3.	When the transfer is initiated from an external source, the external source shall specify the Transaction ID and this shall then be used through the process. When the transfer is initiated by the requesting federate, the requesting federate shall specify the Transaction ID and this shall then be used through the process.
Parameter: TMR.RequestFederate
4.	The Federate Name shall specify the federate that makes the request for the transfer.
Parameter: TMR.ResponseFederate
5.	The Federate Name shall specify the federate that is the responding federate.

#### Interaction: TMR_RequestTransferModellingResponsibility
1.	Request Transfer Modelling Responsibility shall be sent from the requesting federate to the responding federate, these federates are specified in the inherited parameters from the super interaction. If the request is the result of a TMR_Initiate
TransferModellingResponsibility interaction, the parameters from that interaction shall be copied and used in the request.
Parameter: RequestTransferModellingResponsibility.TransferType
2.	An enumerated value that shall indicate the direction of the transfer on the ownership and whether there shall be any negotiation:
Acquire
a.	Requesting Federate acquires instance attribute ownership from the Responding Federate (current owner).
Divest
a.	Requesting Federate (current owner) releases instance attribute ownership to Responding Federate.
AcquireWithoutNegotiating
a.	Requesting Federate acquires unowned instance attributes.
Parameter: RequestTransferModellingResponsibility.Instances
3.	The Instances parameter shall specify the instances in the transfer collected in an array. The UniqueId attribute (UUID) is used for entity reference. The UniqueId attribute is defined in NETN object classes.
Parameter: RequestTransferModellingResponsibility.Attributes
4.	The Attributes parameter shall specify the common set of attributes for all instances that shall be involved in the transfer. The set is collected in an array. An attribute shall be specified by the attribute name.
Parameter: RequestTransferModellingResponsibility.CapabilityType
5.	The CapabilityType is an enumerated value and shall specify the capability type that the transfer is about. The usage of this is optional with a default value of Other. Some federates may be dependent on a value other than Other. There shall be a correspondence between the capability type and the set of attributes.
6.	Enumerated values:
Total
a.	Intersection of published attributes of the object class at the acquiring and divesting federate.
Movement
a.	E.g. Spatial, PowerPlantOn, etc.
Damage
a.	E.g. DamageState, Immobilized, etc.
Resource Consumption
Other
Parameter: RequestTransferModellingResponsibility.InstanceAttributeValues
7.	Optional parameter, default value is an empty array. Shall be used when acquiring federate is unaware of current instance attribute values, e.g. re-entering federates.

#### Interaction: TMR_OfferTransferModellingResponsibility
1.	Offer Transfer Modelling Responsibility shall be sent from the responding federate to the requesting federate; these federates are specified in the inherited parameters from the super interaction. If the transfer is initiated from an external source, with the interaction TMR_InitateTransferModellingResponsibility, the requesting federate shall respond with TMR_OfferTransferModellingResponsibility to inform the originator of the intention of the initiate.
Special Case:
2.	When the transfer type is Divesting, the delivery order of the interaction TMR_OfferTransferModellingResponsibility and the HLA ownership callback service requestAttributeOwnershipRelease at the receiving federate is not determined. Due to this, receiving a requestAttributeOwnershipRelease callback should be treated in the same way as receiving a TMR_OfferTransferModellingResponsibility with a positive offer.
3.	The user supplied tag in the callback service contains the transaction identification which identifies a specific transfer process.
Parameter: OfferTransferModellingResponsibility.isOffering
4.	Definition of the parameter values:
True
a.	If and only if for all instances all attributes in the request are offered.
False
a.	If for any instance any attribute in the request is not offered.
Parameter: OfferTransferModellingResponsibility.Respondent
5.	Shall specify the sender of the offer interaction using the Federate Name.
Parameter: OfferTransferModellingResponsibility.Reason
6.	An enumerated value that shall specify the reason for a negative offer:
a.	Other.
b.	CapabilityDoesNotMatch.
c.	AttributeSetTooRestricted.
d.	AttributeSetTooExtensive.
e.	FederateTooBusy.
f.	AttributeSetNotCompatibleWithPublication.
g.	OwnershipStateNotApplicableWithRequest.
h.	EntityNotKnown.
7.	The usage is optional with a default value of Other.

#### Interaction: TMR_InitiateTransferModellingResponsibility
1.	This interaction shall trigger the requesting federate to do the request for modelling responsibility transfer.
Parameter: TMR_InitiateTransferModellingResponsibility.Initiating
2.	The Initiating parameter shall specify the originator of the interaction, e.g. the value may be the federate name or the Callsign for the role possessor.
3.	Other parameters shall be used by the Requesting Federate in the request interaction.
Parameter: TMR_InitiateTransferModellingResponsibility.TransferType
4.	See Parameter: RequestTransferModellingResponsibility.TransferType.
Parameter: TMR_InitiateTransferModellingResponsibility.Instances
5.	See Parameter: RequestTransferModellingResponsibility.Instances.
Parameter: TMR_InitiateTransferModellingResponsibility.Attributes
6.	See Parameter: RequestTransferModellingResponsibility.Attributes.
Parameter: TMR_InitiateTransferModellingResponsibility.CapabilityType
7.	See Parameter: RequestTransferModellingResponsibility.CapabilityType.
Parameter: TMR_InitiateTransferModellingResponsibility.InstanceAttributeValues
8.	See Parameter: RequestTransferModellingResponsibility.InstanceAttributeValues.

#### Interaction: TMR_CancelRequest
1.	Sent by the Requesting Federate to cancel a request.
Parameter: TMR_CancelRequest:Reason
2.	An enumerated value that describes the reason for the cancellation:
Other
a.	When a Requesting Federate for some reason except time out decides not to complete a transfer, a cancel request shall be sent from the Request Federate to the Response Federate.
TimeOut
a.	When a model's time limit for receiving a TMR Offer has passed, a cancel of the request shall be sent from the Request Federate to the Response Federate.

#### Interaction: TMR_TransferResult
1.	Sent by the Requesting Federate, receiver is the initiating federate.
Parameter: TMR_TransferResult.TransferOk
2.	A Boolean value indicating the result of the transfer.

### Use Cases
A number of different cases are described with sequence diagrams in this chapter.
 
Figure 5-2: The TMR interactions and HLA services are colour coded.
 
#### Acquire Request and a Positive Offer
 
Figure 5-3: TMR Acquire – OK. The requesting federate initiates 
the transfer to acquire instance attributes, transfer successful.
5.2.4.2.	Transfer Request and a Negative Offer
The transfer type can be either Acquire or Divest in this case.
 
Figure 5-4: The Requesting Federate Initiates the Transfer to 
Acquire or Divest Instance Attributes, No Transfer Done.
 
#### Request and Cancel Request 
The requesting federate initiates the transfer but for some reason decides to cancel the request, e.g. a time out due to no offer from the response federate.
 
Figure 5-5: TMR CancelRequest – 1. The requesting federate initiates the transfer to acquire instance attributes, thereafter cancelled by the requesting federate.

#### Request, Positive Offer and Cancel Request 
The requesting federate initiates the transfer but for some reason decides to cancel the request after a positive offer from the response federate.
 
Figure 5-6: TMR CancelRequest – 2. The requesting federate initiates the transfer to acquire instance attributes, a positive offer from the response federate, thereafter cancelled by the requesting federate.

#### Divest Request and Positive Offer 
The requesting federate initiates the transfer for divesting instance attributes.
 
Figure 5-7: TMR Divest – OK. The requesting federate initiates the 
transfer to divest instance attributes, transfer successful.

#### Divest Request and Positive Offer, Race Condition 
The requesting federate initiates the transfer for divesting instance attributes, the callback service is delivered before the positive offer interaction, and the callback is treated as a positive offer. The requesting federate does not need to wait for the TMR_OfferTransferResponsibility interaction to send the HLA service attributeOwnershipDivestureIfWanted. The UserSuppliedTag contains the transaction id and is bound to the original request.
 
Figure 5-8: TMR Divest – OK – Race. The callback 
service is treated as an implicit positive offer.

#### Divest Request, Positive Offer, Cancel Request After HLA Ownership Negotiation Started 
The requesting federate initiates the transfer for divesting instance attributes, the offer is positive but requesting federate cancels the request after the response federate has called attributeOwnershipAcquisition. The response federate has to cancel the acquisition with HLA service cancelAttributeOwnershipAcquisition.
 
Figure 5-9: TMR CancelRequest – 3. The requesting federate initiates the transfer to divest instance attributes, a positive offer from the response federate, thereafter cancelled by the requesting federate.

#### Initiate from External Source, Acquire Request, Positive Offer
The requesting federate starts the acquiring transfer after an initiate from an external source. The requesting federate sends a positive offer to the initiating federate and a report that the transfer was OK after it is completed.
 
Figure 5-10: The Trigger Federate Initiates the Transfer 
to Acquire Instance Attributes, Transfer Successful.
 
#### Initiate from External Source, Divest Request, Positive Offer
The requesting federate starts the divesting transfer after an initiate from an external source. The requesting federate sends a positive offer to the initiating federate and a report that the transfer was OK after it is completed.
 
Figure 5-11: The Trigger Federate initiates the Transfer 
to Divest Instance Attributes, Transfer Successful.

#### Initiate from External Source, Acquire Request, Positive Offer and Cancel Request 
The requesting federate starts the acquiring transfer after an initiate from an external source. The requesting federate sends a positive offer to the initiating federate. A report that the transfer failed is sent after the cancellation.
 
Figure 5-12: The Trigger Federate Initiates the Transfer to Acquire or 
Divest Instance Attributes, a Positive Offer from the Requesting 
Federate, Thereafter Cancelled by the Requesting Federate.

#### Initiate from External Source, AcquireWithoutNegotiating Request
The requesting federate starts the acquiring transfer after an initiate from an external source. The requesting federate sends a positive offer to the initiating federate and a report that the transfer was OK after it is completed.
 
Figure 5-13: The Trigger Federate Initiates the Transfer 
to Acquire Instance Attributes Without Negotiation.
