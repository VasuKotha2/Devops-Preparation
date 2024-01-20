* VPC Stands for Virtual Private Network
* VPC is used to launch AWS resources in a logically isolated virtual network that you've defined.

## Subnets:
* Within a VPC, you can create multiple subnets. Subnets allow you to divide your VPC IP address range into smaller segments, and each subnet can be associated with an availability zone.

## IP addressing:
* You can allocate both IPv4 and IPv6 addresses to your VPCs and subnets. You can also bring your IPv4 and IPv6 addresses and attach to the resources in your VPC.

## Routing:
* We can use route tables to determine where network traffic from your subnet or gateway is directed.

## Gateways and endpoints:
* A gateway connects your VPC to another network. For example, use an internet gateway to
connect your VPC to the internet. Use a VPC endpoint to connect to AWS services privately,
without the use of an internet gateway or NAT device.

## Peering connections:
* Use a VPC peering connection to route traffic between the resources in two VPCs

## Traffic Mirroring:
* Copy network traffic from network interfaces and send it to security and monitoring appliances for deep packet inspection.

## Transit gateways:
* Use a transit gateway, which acts as a central hub, to route traffic between your VPCs, VPN connections, and AWS Direct Connect connections.

## VPC Flow Logs:
* A flow log captures information about the IP traffic going to and from network interfaces in your VPC.

## VPN connections:
* Connect your VPCs to your on-premises networks using AWS Virtual Private Network (AWS
VPN).