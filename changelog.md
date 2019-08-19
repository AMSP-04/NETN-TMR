## Changelog NETN-TMR

### Changes for v2.0 (RC 1)


#### NETN-MRM#4 Make MRM not depend on TMR
* Removed datatype `FederateName` (moved to NETN-BASE).
* Removed datatype `CancellationReasonEnum32` (moved to NETN-BASE).

#### NETN-TMR#1 Move datatype TransactionId to NETN-Base
* Removed datatype TransactionId (moved to NETN-Base).

#### NETN-TMR#2 Update modelIdentification
* Change `modelIdentification` `securityClassification` from `unclassified` to `Not Classified`
* Change `modelIdentification` `other` to include license information
* Change `modelIdentification` `reference` to only refer to directly dependent FOM Modules
* Add `modelIdentification` `useLimitation` to reflect Scope of FOM Module
* Add `modelIdentification` `glyph` 
* Update `modelIdentification` `purpose` to reflect Purpose of FOM Module 
* Update `modelIdentification` `description` to reflect Introduction of FOM Module


#### NETN-TMR#4 Update Introduction documentation
* Introduction section restructured and clarified.

#### NETN-TMR#9 Update TMR PATTERN USAGE incl. seq. diagrams
* Split section into Transfer of Modelling Responsibility Pattern and Use Cases
* Structured interaction class descriptions
* Added seqence diagram and text for basic TMR pattern
* Added seqence diagrams for Negotiated Acquisition, Negotiated Divetiture and non-negotiated Acquisition
* Merged and simplified Cancellation diagrams

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