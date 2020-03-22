## Changelog NETN-TMR

### Changes for v2.0

#### NETN-MRM#4 Make MRM not depend on TMR
* Moved datatype `FederateName` to NETN-BASE.
* Moved datatype `CancellationReasonEnum32` to NETN-BASE.
* Removed NETN-MRM dependency on NETN-TMR.

#### NETN-TMR#1 Move datatype TransactionId to NETN-Base
* Moved datatype TransactionId to NETN-Base

#### NETN-TMR#2 Update modelIdentification
* Changed `modelIdentification` `securityClassification` from `unclassified` to `Not Classified`
* Changed `modelIdentification` `other` to include license information
* Changed `modelIdentification` `reference` to only refer to directly dependent FOM Modules
* Added `modelIdentification` `useLimitation` to reflect Scope of FOM Module
* Added `modelIdentification` `glyph` 
* Updated `modelIdentification` `purpose` to reflect Purpose of FOM Module 
* Updated `modelIdentification` `description` to reflect Introduction of FOM Module

#### NETN-TMR#4 Update Introduction documentation
* Introduction section restructured and clarified.

#### NETN-TMR#5 Rename objectClass TMR to TMR_Root or TMR_Base
* Changed InteractionClass `TMR` to `TMR_Interaction` and renamed parameter `TransactionID` to `TransferId`

#### NETN-TMR#6 Drop or clarify use of capabilityType parameter
* Remove Parameter `CapabilityType` from InteractionClass `TMR_RequestTransferModellingResponsibility`
* Remove Parameter `CapabilityType` from InteractionClass `TMR_InitiateTransferModellingResponsibility`
* Remove EnumeratedDatatype `CapabilityTypeEnum32`

#### NETN-TMR#7 Remove parameter InstanceAttributeValues
* Remove Parameter `InstanceAttributeValues` from InteractionClass `TMR_RequestTransferModellingResponsibility`
* Remove Parameter `InstanceAttributeValues` from InteractionClass `TMR_InitiateTransferModellingResponsibility`
* Remove ArrayDatatype `ArrayOfInstanceAttributeValues`
* Remove ArrayDatatype `ArrayOfAttributeValues`
* Remove ArrayDatatype `ArrayOfBytes`
* Remove FixedRecordDatatype `InstanceAttributeValuesStruct`
* Remove FixedRecordDatatype `AttributeValueStruct`

#### NETN-TMR#8
* Remove Parameter `Respondent` from InteractionClass `TMR_OfferTransferModellingResponsibility`

#### NETN-TMR#9 Update TMR PATTERN USAGE incl. seq. diagrams
* Split section into Transfer of Modelling Responsibility Pattern and Use Cases
* Structured interaction class descriptions
* Added seqence diagram and text for basic TMR pattern
* Added seqence diagrams for Negotiated Acquisition, Negotiated Divetiture and non-negotiated Acquisition
* Merged and simplified Cancellation diagrams

#### NETN-TMR#10 Restructure and simplify FOM interactions
* Changed InteractionClass `TMR_OfferTransferModellingResponsibility` to `OfferTransfer`
* Changed InteractionClass `TMR_RequestTransferModellingResponsibility` to `RequestTransfer`
* Changed InteractionClass `TMR_CancelRequest` to `CancelRequest`
* Changed InteractionClass `TMR_TransferResult` to `TransferResult` and parameter `TransferOk` to `IsCompleted`
* Changed InteractionClass `TMR_InitiateTransferModellingResponsibility` to `InitiateTransfer`

#### NETN-TMR#11 Naming of datatype NoofferReasonEnum32 and enumerations
* Changed name of EnumeratedDatatype `NoofferReasonEnum32` to `NoOfferReasonEnum32` and enumeration `OwnershipStateNotApplicableWithRequest` to `OwnershipStateNotCompatibleWithRequest`

#### NETN-TMR#12 Change datatype of Initiating to FederateName
* Changed Datatype of Parameter `Initiating` of InteractionClass `TMR_InitiateTransferModellingResponsibility` from `HLAunicodeString` to `FederateName`
* Changed Name of Parameter `Initiating` of InteractionClass `TMR_InitiateTransferModellingResponsibility` to `InitiatingFederate`

#### NETN-TMR#15 Update to comply with Naming Conventions
* Change name of EnumerateDatatype `TransferTypeEnum32` to `TransferEnumType`
* Change name of EnumerateDatatype `NoOfferReasonEnum32` to `NoOfferReasonEnumType`
* Change name of ArrayDatatype `ArrayOfAttributes` to `AttributeNamesType`
* Change paramter `isOffering` of InteractionClass `TMR_OfferTransferOfModellingResponsibility` to `IsOffering`


### Changes for v1.1.3

v1.0.1 XML Schema Reference Changed
v1.0.2 - Spelling correction at enumerations
v1.0.3 - Adding AttributeValues
v1.0.3r3 - Adding reason
v1.0.3r4 - Added parameter Respondent at interaction TMR_OfferTransferModellingResponsibility and enumeration value NoofferReasonEnum32.OwnershipStateNotApplicableWithRequest
v1.0.3r5 - Added enumeration value NoofferReasonEnum32.EntityNotKnown
V1.0.3r6 - Change definition of data type TransactionId, a counter and the federate handle
v1.1.0r1 - Added interactions TMR_CancelRequest and TMR_Status
v1.1.0 - Removed "r1" from module name
v1.1.1 - Update of Dependecy table
v1.1.2 - Rename of enumeration values (AttributeSetTooRestricted, AttributeSetTooExtensive).
v1.1.3 - Rename of enumeration value (FederateTooBusy).