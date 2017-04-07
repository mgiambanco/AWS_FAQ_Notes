VPC

[AWS VPC FAQ](https://aws.amazon.com/vpc/faqs/)

Virtual Private Cloud

* Connect a VPC to:
    * Internet via an Internet Gateway
    * Corporate Data Center via Virtual Private Gateway
    * Both Internet and Corporate
    * Other AWS services (via Internet Gateway, NAT, Virtual Private Gateway or VPC endpoints)
    * Other VPCs (via VPC Peering)
* No bandwidth constraints
* Instances WITHOUT a public IP can be route traffic via NAT
* Does NOT enforce VPN Throughput limitations - other factors may impact this though
* VPC uses IPv4 and IPv6
* Can have BOTH IPv4 and IPv6 subnets
* To change a VPC size, it must be terminated and re-created
* Can create 200 subnets per VPC - submit a case if you need more - https://aws.amazon.com/contact-us/vpc-request/
* Minimum subnet size is /28 (14 addresses for IPv4) and /64 for IPv6
* AWS reserves the first 4 IP addresses and the last 1 IP address for networking of EVERY subnet you create
* Use Security Groups to secure a VPC
* Access Control Lists (ACLs) can also be used
* Ping to the router in a VPC is disabled
* Use VPC Flow Logs to monitor network traffic in a VPC
* A VPC CAN span Multiple AZs
* A subnet can NOT span Multiple AZs
* Specify the AZ when launching the VPC
* If an Instances communicating with each other are in different AZs, a data transfer charge of $0.01 per GB applies
* Instances in a VPC are limited to the size of the VPC - each instances needs an IP address
* An Instance inside of a VPC retains it's IP address when started and stopped
* Can use CloudWatch to monitor a VPC
* Can use Auto Scale with a VPC
* Cluster Instances can be used in a VPC
* A VPN connection is NOT required to use a VPC
* Multiple VPCs can be created
* ONLY 1 Default VPC can exist
* The default VPC CIDR is 172.31.0.0/16. Default subnets use /20 CIDRs within the default VPC CIDR.
* You can NOT change the Default VPC
* Contact AWS support if you deleted your Default VPC and want a new one
* Network interfaces CAN be attached or detached while an EC2 instance is running
* Network interfaces can only be attached to instances in the same AZ
* Network interfaces can only be attached to instances in the same VPC as the interface
* You can NOT detach ETH0 from an EC2 instance
* Peering connections are ONLY available between VPCs in the same Region
* A VPC CAN be peered with another VPC in a different AWS account, assuming the owner of the other VPC account accepts your connection request
* Peered VPCs must have NON-OVERLAPPING IP ranges
* There is no charge for a VPC - only the bandwidth and resources it consumes
* Edge to Edge routing is NOT supported
* Traffic between peered VPCs is NOT encrypted
* Transitive Peering is NOT supported
* ClassicLink allows EC2 Classic instances to communicate with EC2 instances inside of a VPC
* The EC2 Classic instance does NOT become a member of the VPC. It becomes a member of the VPC Security Group
