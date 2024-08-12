# Campus Network Configuration

## Overview

This repository contains the documentation for the configuration and implementation of the International Travel Agency's switched network. The project involved configuring a complex network environment that includes multiple VLANs, EtherChannels, HSRP for redundancy, and various security features.

## Contents

- **Documentation**: Detailed steps and configurations implemented in the network, including the topology, VLAN configuration, EtherChannel setup, HSRP configuration, and security features.
- **Verification and Testing**: A comprehensive report on the verification and testing process conducted to ensure the network operates as expected.
- **Configuration Files**: All necessary configuration commands used during the setup, which can be referenced or re-used as needed.

## Requirements

The network configuration was designed using Cisco hardware with the following prerequisites:

- Cisco switches supporting Layer 2 and Layer 3 functionalities.
- Knowledge of VLAN, STP, HSRP, EtherChannel, VTP, EIGRP, ACLs, and security configurations.
- Access to Cisco CLI for configuration and testing.

## How to Use

1. **Review the Documentation**: Start by reading the documentation to understand the network topology, configuration details, and the security measures implemented.
2. **Apply Configurations**: Use the provided configuration files or commands within the documentation to replicate the setup on your lab equipment.
3. **Test the Network**: Follow the verification and testing procedures outlined in the documentation to ensure your configuration is functioning as intended.
4. **Troubleshoot**: If any issues arise, refer to the detailed steps in the documentation for troubleshooting tips and solutions.

## Key Features

- **Layer 3 EtherChannel**: Configured using LACP between distribution switches.
- **VLAN Segmentation**: Multiple VLANs configured for staff, students, management, and voice.
- **HSRP for Redundancy**: Ensured high availability with HSRP configured for critical VLANs.
- **Security Features**: Implemented PortFast, BPDUguard, UDLD protection, DHCP snooping, and port security.

## Verification and Testing

The network was thoroughly tested to ensure all configurations were operational. The tests included:

- **Connectivity Tests**: Verified ping responses across all VLANs and interfaces.
- **HSRP Failover**: Simulated failover scenarios to ensure redundancy mechanisms worked correctly.
- **Security Tests**: Checked PortFast, BPDUguard, and UDLD responses to ensure network resilience.

## Support

For any questions or issues related to this case study, feel free to reach out. The documentation includes all necessary information to replicate and troubleshoot the setup.

