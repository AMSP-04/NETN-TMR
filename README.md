# NETN-TMR

NATO Education and Training Network (NETN) Transfer of Modelling Responsibilities (TMR) Module

## Introduction

In a federated distributed simulation the participating systems (federates) collectively model the synthetic environment. Allocation of modelling responsibilities are based on individual federate capabilities, federation design agreements, and initial scenario conditions. The responsibility of updating an attribute for a specific simulated entity is allocated to at most one federate. However, during execution the modelling responsibility may change and the ownership of attributes can be transferred. 

Basic services for the divestiture and acquisition of attribute ownership is provided by IEEE 1516 High Level Architecture (HLA). A negotiated and coordinated transfer of modelling responsibilities requires agreements between federates before attribute ownership is transferred. 

The NATO Education and Training Network Transfer of Modelling Responsibilities (NETN-TMR) FOM Module is a specification of how to perform a negotiated and coordinated transfer of attribute modelling responsibility between federates in a distributed simulation. 

The specification is based on IEEE 1516 High Level Architecture (HLA) Object Model Template (OMT) and primarily intended to support interoperability in a federated simulation (federation) based on HLA. A Federation Object Model (FOM) Module is used to specify how data is represented and exchanged in the federation. The NETN-TMR FOM module is available as an XML file for use in HLA based federations.

### Purpose

The NETN-TMR FOM module provides a standard interface and protocol for conducting negotiated and coordinated transfer of attribute modelling responsibility between federates. It extends the HLA Ownership Management services by providing the means to 
1. Negotiate the transfer of ownership. 
2. Initiate ownership transfer using a Trigger federate.

A transfer of modelling responsibility is perfomed during runtime, to dynamically change the responsibility to update specific attributes, to a more suitable federate.

For example: 
- Transfer from a Live to a Virtual or Constructive simulation
- Transfer between Virtual and Constructive simulations
- Transfer between hi- and low-fidelity models
- Transfer to allow backup, maintenance or load-balancing
- Transfer of certain attributes to functional models such as movement, damage assessment etc.

### Scope

NETN-TMR covers the following cases:

* Negotiated acquisition where a federate requests to receive the modelling responsibility 
* Divestiture where a federate requests another federate to take modelling responsibility
* Acquisition without negotiation where a federate receives the modelling responsibility
* Cancellation of transfer

## License

Copyright (C) 2019 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENSE.md). 

The work includes the [NETN-TMR.xml](NETN-TMR.xml) FOM Module and documentation NETN-TMR.md.

Above license gives you the right to use and redistribute the NETN FOM Module (XML file and Documentation) in its entirety without modification. You are also allowed to develop your own new FOM Modules (in separate XML files and separate documentation) that build-on/extends the NETN module by reference and including neccessary scaffolding classes. You are NOT allowed to modify this FOM Module or its documentation without prior permission by the NATO Modelling and Simulation Group. 

## Versions, updates and extentions

All updates and versioning of this work is coordinated by the NATO Modelleing and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitGub issue tracking. To engage in the development and update of this FOM Module please contact your national NMSG representative.

Version numbering of this FOM Module and associated documentation is based on the following principles:

* New official version number is assigned and in effect only when new release is made in the Master branch.
* Updates in the Develop branch will not change version number.
* In the FOM Module useHistory information include only information on official releases.
* Update of the major version number is made if the change constitute a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or cover entirely new concepts.
* Update of the minor version number is made if the change constitute a minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|Description|
|---|---|
|v1.1.3 |Initial version of NETN-TMR FOM Module released as part of NETN-FOM v2.0 in AMSP-04 Ed A. |
|v2.0.0 RC1 | Released version part of NETN-FOM v3.0 in AMSP-04 Ed B. |

[Changelog](changelog.md)

## Documentation

[Full Documentation](NETN-TMR.md)
