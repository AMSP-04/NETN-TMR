# NETN-TMR


|Version| Date| Dependencies|
|---|---|---|
|3.0|2023-11-18|NETN-BASE, NETN-ORG, NETN-ETR|

> [Full Documentation](NETN-TMR.md)

The NATO Education and Training Network Transfer of Modelling Responsibilities (NETN-TMR) FOM module provides a standard interface and pattern for transferring modelling responsibility between federates. It extends the HLA Ownership Management services by providing the means to trigger the transfer of modelling responsibility and to publish the assigned modelling responsibilities of object instances.
        
For example:
            
* Transfer modelling responsibility between virtual and constructive simulation systems  
* Transfer modelling responsibility between high- and low-fidelity models  
* Transfer modelling responsibility to allow backup, maintenance or load-balancing

In a federated distributed simulation, the participating systems (federates) provide services that model the synthetic environment. Allocation of modelling responsibilities depends on individual federate capabilities, federation design agreements, and initial scenario conditions. The primary responsibility for modelling a simulated entity is allocated to, at most, one federate. However, during execution, the modelling responsibility and ownership of individual attributes may change.

NETN-TMR covers the following cases:            
* Initialization with assigned modelling responsibilities for objects 
* Explicit request to acquire modelling responsibility 
* Triggering of modelling responsibility transfer by updating the allocation of responsibility attribute

## Licence

Copyright (C) 2020 NATO/OTAN.
This work is licensed under a [Creative Commons Attribution-NoDerivatives 4.0 International License](LICENCE.md). 

The work includes the [NETN-TMR.xml](NETN-TMR.xml) FOM Module and documentation NETN-TMR.md.

Above licence gives you the right to use and redistribute the NETN FOM Module (XML file and Documentation) in its entirety without modification. You are also allowed to develop your FOM Modules (in separate XML files and separate documentation) that build-on/extends the NETN module by reference and including necessary scaffolding classes. You are NOT allowed to modify this FOM Module or its documentation without prior permission by the NATO Modelling and Simulation Group. 

## Versions, updates and extensions

All updates and versioning of this work is coordinated by the NATO Modelling and Simulation Coordination Office (MSCO), managed by the NATO Modelling and Simulation Group (NMSG) and performed as NATO Science and Technology Organization (STO) technical activities in support of the NMSG Modelling and Simulation Standards Subgroup (MS3).

Feedback on the use of this work, suggestions for improvements and identified issues are welcome and can be provided using GitHub issue tracking. To engage in the development and update of this FOM Module please contact your national NMSG representative.

Version numbering of this FOM Module and associated documentation is based on the following principles:

* New official version number is assigned and in effect only when a new release is made in the Master branch.
* Updates in the Develop branch will not change the version number.
* In the FOM Module `useHistory` information includes only information on official releases.
* Update of the major version number is made if the change constitutes a major restructuring, merging, addition or redefinition of semantics that breaks backward compatibility or cover entirely new concepts.
* Update of the minor version number is made if the change constitutes minor additions to existing concepts and editorial changes that do not break backward compatibility but may require updates of software to use new concepts.
* Patches are released to fix minor issues that do not break backward compatibility.

|Version|Description|
|---|---|
|v1.1.3 | Initial version of NETN-TMR FOM Module released as part of NETN-FOM v2.0. |
|v2.0.0 | Updated version part of NETN-FOM v3.0. |

[Changelog](changelog.md)

## Documentation

[Full Documentation](NETN-TMR.md)
