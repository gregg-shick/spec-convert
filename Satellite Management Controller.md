
# Open Compute Project  



##### Satellite Management Controller
##### (Auxiliary Management Controller)

##### Revision 1.0, Version 1.0


##### Base Specification


Author: Chad Yoshikawa  
Author: Ed Tanous  
Author: Jeff Hilland  
Author: Gregg Shick  
Author: Patrick Williams  
Author: Changho Choi  
Author: Kavin Lee  
Author: BJ Kim  
Author: Mike Allison  

### Table of Contents

Insert this

### Glossary of Terms

This section provides definitions for terms used in this document.  

**Server**. Machine hardware that contains a Satellite plug-in. Satellite containers are
typically Servers but are not required to be so. So we use the more general term Host for a Satellite
container.  

**Host**. A generalization of a Satellite container that includes Servers (for PCIe Plug-In
Satellites) and motherboards (for SoC Satellites). A Host is managed by a logical Host Management
Controller (HMC).  

**Satellite**. A dependent group of hardware that is managed by a logical Satellite
Management Controller (SMC). Satellites typically are smaller than their Host, are terminal points
in the management graph, and contain a single power & thermal domain.  

**SMC**. Satellite Management Controller provides a management API to Satellite hardware.
SMCs may be backed by one or more discrete hardware components. SMC is typically a low-cost
ARM microcontroller running a RTOS with no external DRAM, although this is not prescriptive and
any CPU architecture and configuration is acceptable.  

**Terminal Hardware**. Hardware that is an endpoint in the management graph. In other
words, terminal hardware does not itself manage other hardware. Satellites are terminal hardware.

### 1. License
INSERT THIS
### 1.2 Acknowledgements
The Contributors of this Specification would like to acknowledge the following companies for their feedback:

Hewlett Packard Enterprise  
Google  
Samsung  
Dell  
Meta

### 1.3 References
Insert this

### 2. Compliance with OCP Tenants
#### 2.1 Openness
The SMC V1.0 specification proposes an ecosystem-enabling set of requirements for peripherals to
enable management compatibility between open systems. This allows interoperability between
various device classes and host systems.  
#### 2.2 Efficiency
OEMs invest time to create specifications for industry Independent Hardware Vendors (IHVs)
which must be implemented in order to support proper management by the host. IHVs invest
time working with multiple OEMs to implement those requirements. The goal of the SMC
specification is to standardize those various work streams into a single public OCP specification
where both OEM and IHV can more effectively promulgate these requirements.
Additionally, multi-vendor customer environments will benefit from the efficiencies achieved
through increased device interoperability and the utilization of a common code base for system
management.
#### 2.3 Impact
The SMC represents a single set of OCP device manageability requirements allowing for IHV
ease of development, time to market, and effective use of engineering resources. Device
management ASICs could be developed allowing multiple IHVs to leverage a standardized SMC
component providing consistent management across device classes.
#### 2.4 Scale
Large scale deployments benefit from the standardization of management capability across
multiple device classes, server and device vendors which this specification provides.  

Redfish, RDE and PLDM DMTF standards for management are utilized allowing for a common
set of APIs and management tools regardless of hardware or software environment or size of
server deployment.
#### 2.5 Sustainability
Between customers’ sustainability initiatives and demands to control energy consumption and
costs, the ability to report, analyze and actuate server power usage data has become a key
initiative.  

The creation of a truly interoperable telemetry environment will allow businesses to datacenters,
no matter the size, to more effectively meet sustainability targets. SMC thermal and power
management capabilities can be utilized to enable this goal of minimizing power requirements
and overall energy usage
### 3. Change Log
Insert this

### 4. Overview
The Satellite Management Controller specification defines a validatable management interface
between a satellite container (“server” or more generally a “host”) and simple hardware plug-ins
(“satellites”). For example, for a server and PCIe plug-in card, the host server manages the satellite
plug-in.  

Satellites are simple: they do not manage other devices and typically contain a single thermal,
power and security domain. Note that the satellite and host may not be discrete hardware; host and
satellite may be integrated onto the same board in the case of a tray and its SoC.  

Satellite conformance can be validated using software tools, which enables independent hardware
development and bring-up. To provide validation, the SMC specification defines a compatibility
test suite (CTS) to ensure conformance to specified functional requirements.  

The management interface additionally specifies SLOs for operations such as firmware update and
power management operations. These SLOs may impose constraints on the underlying hardware.
For example, timely firmware update may require i3c (vs. i2c) or higher-bandwidth management
links.  

#### 4.1 Architectural Example

**insert pic here**

SMC includes all API definitions required for managing a peripheral device from an out of band
management controller (BMC) in the most common configuration. While other configurations may
exist that this specification fulfills, the above diagram is considered the baseline. This specification
may reference elements of the baseline configuration as examples. Other configurations may exist.  

The SMC specification explicitly does not define any physical connectors, physical form factors, or
specifications for non SMC components, although other specifications (such as the [Modular
Hardware Management DC-SCM](https://www.opencompute.org/documents/ocp-dc-scm-spec-rev-1-0-pdf)) may define connector specifications that may be used in
deployments. For some examples, this specification may assume a PCIe 16X connector, and a single
socket server with BMC.


### 5. Protocols

SMC devices *shall* implement DSP0236 (Management Component Transport Protocol (MCTP) Base Specification).

### 6. API Surface







