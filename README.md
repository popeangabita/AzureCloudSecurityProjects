# Azure Network Security Project

## Objective
Design a secure network topology with Network Security Groups (NSGs) and Azure Firewall to control access and protect resources.

## Skills Highlighted
- Network Security
- NSG Rules
- Firewall Configuration
- Access Control

## VNet Configuration
- **VNet Address Space**: `10.0.0.0/16`
  - **Subnet1 (Application Servers)**: `10.0.1.0/24`
  - **Subnet2 (Database Servers)**: `10.0.2.0/24`
  - **AzureFirewallSubnet**: `10.0.3.0/24`
  - **AzureFirewallManagementSubnet**: `10.0.4.0/24`

## Steps Overview
1. **Create a Virtual Network (VNet)**:
   - Set up the VNet with the address space `10.0.0.0/16` and the specified subnets.
   
2. **Set Up Network Security Groups (NSGs)**:
   - Configure NSGs to control inbound and outbound traffic on specific subnets.

   ### NSG Rules Configuration

   #### Inbound Rules for Application Subnet (10.0.1.0/24)
   1. **Allow HTTP**
      - Source: Any
      - Destination: 10.0.1.0/24
      - Protocol: TCP
      - Port: 80
      - Action: Allow

   2. **Allow HTTPS**
      - Source: Any
      - Destination: 10.0.1.0/24
      - Protocol: TCP
      - Port: 443
      - Action: Allow

   #### Inbound Rules for Database Subnet (10.0.2.0/24)
   1. **Allow SQL Server**
      - Source: 10.0.1.0/24
      - Destination: 10.0.2.0/24
      - Protocol: TCP
      - Port: 1433
      - Action: Allow

   #### Outbound Rules
   1. **Deny All Outbound**
      - Source: Any
      - Destination: Any
      - Action: Deny

3. **Add Azure Firewall**:
   - Implement Azure Firewall to filter traffic between subnets and control access to the internet.

   ### Azure Firewall Configuration

   #### Firewall Rules
   1. **Allow HTTP and HTTPS to the Internet**
      - Source: 10.0.1.0/24
      - Destination: Internet
      - Protocol: TCP
      - Ports: 80, 443

   2. **Allow SQL Access Between Subnets**
      - Source: 10.0.1.0/24
      - Destination: 10.0.2.0/24
      - Protocol: TCP
      - Port: 1433
