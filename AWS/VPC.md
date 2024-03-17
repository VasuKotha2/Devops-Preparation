## Basics:
----------
IP Address:
-----------
* Represented in dotted decimal format.
* Five classes of IPv4 Address:
    * Class A: First bit starts with 0(BINARY NOTATION) or First byte contains between 0-127 (DOTTED DECIMAL NOTATION)
    * Class B: First bits starts with 10(BINARY NOTATION) or First byte contains between 128-191 (DOTTED DECIMAL NOTATION)
    * Class C: First bits starts with 110(BINARY NOTATION) or First byte contains between 192-223 (DOTTED DECIMAL NOTATION)
    * Class D: First bits starts with 1110(BINARY NOTATION) or First byte contains between 224-239 (DOTTED DECIMAL NOTATION)
    * Class E: First bits starts with 1111(BINARY NOTATION) or First byte contains between 240-255 (DOTTED DECIMAL NOTATION)
* Two types of Addressing :
  * Classful : Does not support Variable length subnet mask
  * Classless : Support Variable length subnet mask


VPC Components:
---------------
* Virtual Private Cloud
------------------------
1. Subnets
2. Route Tables
3. Internet Gateways
4. Egress-only internet gateways
5. Carrier gateways
6. DHCP option sets
7. Elastic IPs
8. Managed prefixed lists 
9. Endpoints
10. Endpoint services
11. NAT Gateways
12. Peering connections

* Security
----------
1. Network ACLs
2. Security groups

* DNS Firewall
--------------
1. Rule groups
2. Domain lists

* Network Firewall
------------------
1. Firewalls
2. Firewall policies
3. Network Firewall rule groups
4. TLS inspection configurations
5. Network Firewall resource groups

* Virtual Private Network (VPN)
-------------------------------
1. Customer gateways
2. Virtual private gateways
3. Site-to-Site VPN Connections
4. Client VPN endpoints

* AWS Verified services
------------------------
1. Verified access instances (New)
2. Verified access trust providers (New)
3. Verified access groups (New)
4. Verified access Endpoints (New)

* Transit gateways
------------------
1. Transit gateways
2. Transit gateway attachments
3. Transit gateway policy tables
4. Transit gateway route tables
5. Transit gateway multicast

* Traffic Mirroring
-------------------
1. Mirror Sessions
2. Mirror targets
3. Mirror filters

* VPC Lattice
-------------
1. Getting Started (New)
2. Service networks (New)
3. Services (New)
4. Target groups (New)

Virtual Private Cloud:
----------------------
1. Subnet:
----------
* Subnet is “part of the network”, in other words, part of entire availability zone. Each subnet must reside entirely within one Availability Zone and cannot span zones.

2. Route Table:
---------------
* A route table contains a set of rules, called routes, that are used to determine where network traffic from your subnet or gateway is directed. To put it simply, a route table tells network packets which way they need to go to get to their destination.

3. Internet Gateway:
-----------------
Internet Gateway (IGW) allows instances with public IPs to access the internet.

4. Egress-only Internet Gateway:
-----------------------------
* Egress-only Internet Gateway is a VPC component that allows outbound only communication to the internet over IPv6, and prevents the Internet from initiating an IPv6 connection with your instances.

5. Carrier gateway:
------------------
* Carrier Gateway is a service that enables AWS customers to establish a direct and private connection between their on-premises data center or network and their Virtual Private Cloud (VPC) on AWS. It allows users to extend their network topology to AWS, thus providing a secure and high-bandwidth connection between their on-premises infrastructure and AWS.


NAT Gateway:
------------
NAT Gateway (NGW) allows instances with no public IPs to access the internet.

IP Address:
-----------
* A unique string of numbers separated by periods that identifies each computer using the Internet Protocol to communicate over a network. Each instance in AWS gets 2 IP address, a private ip address and public ip address.

Security Group:
---------------
* A security group acts as a virtual firewall that controls the traffic for one or more instances. When you launch an instance, you associate one or more security groups with the instance. You add rules to each security group that allow traffic to or from its associated instances.



AWS interview questions on VPC:
-------------------------------
1. When AWS already creates a default VPC, why do we need to create an additional VPC in AWS again?

Ans. VPC means Virtual Private Cloud. By default AWS creates a default VPC in all regions. But the best practice is to create our own VPC because the default VPC is created in public subnet and whenever you create a resource like EC2 instance it will be created in public subnet. Also there is an internet gateway by default connected to the default VPC. But in our production environments we will create public and private subnets to enhance security for our architecture so it is better to create our own VPC.

2. You got a requirement to create a custom VPC in a new AWS account, so what components you will take to design the VPC with security taken into consideration?

Ans. When we get a requirement to create a VPC, 

    1.  Plan your CIDR blocks: We have to plan the proper CIDR blocks. 
        Two things to keep in mind is
            * CIDR blocks you are using are large enough so that we will not run out of ips.
            * your CIDR blocks should not overlap with each other when you are dealing with other AWS VPC's or may be networks that exits outside of AWS may be onprem environment.
    2. Use multiple AZ's
        A VPC is scoped to a region. You want to make sure to build highly Available fault tolerance solutions in AWS that your VPC's span multiple availability zones or Az's in the region where you deploy your VPC
    3. Create multiple layers of defence
        We can achieve this by configuring NACL's which are stateless firewalls that operates at the subnet level and they are optional and then configuring security groups which are stateful firewalls that operate at the elastic network interface level inside your VPC.
    4. Enable VPC flow logs
        Flow logs are going to give you a high level picture of all the traffic flowing either into or out of your VPC. While setting up this you can set up your destination into either cloud watch or S3.
        Preferred destination is cloud watch which makes us easy to troubleshoot the issues faster and easy to create log insights quickly.
    5. Use NAT gateways
        We have to limit as best as we can any public facing resources and to do this we have to configure NAT gateways
    6. Leverage VPC endpoints (Brett Gillett)

3. When we create an EC2 instance by default a public IP gets created. How to stop creating that public IP address?

Ans. While creating an EC2 instance, in the network settings section there will be an option called Auto-assign public IP. By default it will be in enable mode we have to disable it.

Go to subnets and for a particular subnet edit the subnet settings and uncheck the Enable auto-assign public IPv4 Address and save.

4. How to monitor the traffic which is incoming and outgoing?

Ans. We can create a VPC flow log to monitor that. If we want to allow or block any particular traffic we can do that.

5. 
