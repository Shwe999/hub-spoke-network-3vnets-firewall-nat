---
Description: This template builds a secure hub-and-spoke network architecture with Azure Firewall and route tables.
Products: 
- Azure Resource Manager Template
- Azure
Language: 
- Json
---
# Create a Hub with Firewall and Bastion services, and 2 spoke networks, each contains VM, NSG and route table
# Overview & Deployed Resources
## Overview
This template creates a centralized hub-and-spoke network design, ensuring a secure network connection between two spokes through a hub. The design implements a hub VNet containing Azure Firewall and Azure Bastion services, which is peered with two spoke VNets. Each spoke VNet has a Virtual Machine (VM) which can be connected via bastion without exposing public ip address, and custom Route Tables to route traffic between these spokes. Azure Firewall supports as a Virtual Appliance to forward that traffic which is configured with specific policies.

## Resources
### Microsoft.Network
- virtualNetworks - hub, spoke1, spoke2 with subnets
  - hub VNet - subnet1, AzureFirewallSubnet, AzureBastionSubnet
  - spoke1 VNet - subnet-spoke1
  - spoke2 VNet - subnet-spoke2
- virtualNetworkPeerings - for peerings between hub and spoke1, spoke2
- publicIPAddresses - for bastion, firewall, NAT gateway
- bastionHosts - Azure Bastion for secure access to VMs
- firewallPolicies - Firewall Policy with network rules for spoke-to-spoke and spoke-to-internet traffic
- azureFirewalls - Azure Firewall for network security and traffic filtering
- natGateways - NAT gateway for outbound network connectivity
- routeTables - Custom Route tables for spoke to spoke and spoke to internet routes
- networkSecurityGroups - NSGs for VMs in spoke networks
- networkInterfaces - Network Interface for VMs

 ### Microsoft.Compute
 - virtualMachines - Windows Server 2025 Datacenter VMs in each spoke network

`Tags: Virtual Network, VNet, Virtual Network Peering, Azure Firewall, Firewall Policies Azure Bastion, Route Table, NSGs, Network Interface, Virtual Machine, VM, NAT Gateway`
