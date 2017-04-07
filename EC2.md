**EC2**

[AWS EC2 FAQ](https://aws.amazon.com/ec2/faqs/)

Resizable compute capacity in the cloud

* Limit of 20 On-Demand instances
* Limit of 20 Reserved Instances
* You have a Dynamic Spot Instance limit - find it here - http://docs.aws.amazon.com/AWSEC2/latest/UserGuide/using-spot-limits.html
* To request a limit increase, fill in this form - https://aws.amazon.com/support/createCase?type=service_limit_increase&serviceLimitIncreaseType=ec2-instances
* Fill our this form to increase how many email you can send from an EC2 instance - https://portal.aws.amazon.com/gp/aws/html-forms-controller/contactus/ec2-email-limit-rdns-request
* Capacity can be increased within minutes
* EC2 supports:
    * Amazon Linux
    * Ubuntu
    * Windows Server
    * Red Hat Enterprise Linux
    * SUSE Linux Enterprise Server
    * Fedora
    * Debian
    * CentOS
    * Gentoo Linux
    * Oracle Linux
    * FreeBSD
* EC2 uses ECC Memory
* Instances are grouped into 5 families
    * General Purpose
        * Has memory to CPU ratios suitable for most general purpose applications and come with fixed performance (M4 and M3) or burstable performance (T2)
    * Compute Optimized
        * (C4 and C3) have proportionally more CPU resources then memory and are for scale out compute-intensive applications and High Performance Computing (HPC)
    * Memory Optimized
        * (R3 and R4) larger memory size for memory intensive applications including database and memory caching applications
    * GPU
        * (P2) parallel processing capabilities of NVIDIA Tesla GPUs for high performance parallel computing
        * (G2) for high performance 3D graphics capabilities using OpenGL and DirectX
    * Storage Optimized
        * (I3 and I2) very high, low latency, I/O capacity using SSD based local instance storage for I/O intensive applications
        * (D2) High storage density and sequential I/O performance for data warehousing, Hadoop and other data intensive applications
* EC2 is built on commodity hardware
* Use CloudTrail to monitor API access to EC2 instances

**Elastic IP**
* Limited to 5 per region
* Request a limit increase here - https://aws.amazon.com/contact-us/eip_limit_request/
* Theres only so many IPv4 addresses left. IF your instance is NOT running, you will be charged for this IP
* You do NOT need an Elastic IP - every EC2 instances comes with a private and public IP
* It can take several minutes to re-map an Elastic IP
* You can configure a reverse DNS record for an Elastic IP - fill this out - https://portal.aws.amazon.com/gp/aws/html-forms-controller/contactus/ec2-email-limit-rdns-request

**Availability Zones**
* Physically separated data centers with their own power, security, infrastructure
* It is NOT currently possible to coordinate the launch of EC2 instances in the same AZ across 2 AWS accounts

**Enhanced Networking**
* For applications that need high packet-per-second performance and or low latency networking
* Requires a HVM AMI
* No additional fee, but you must select the appropriate instance
* C3, C4, D2, I3, I2, M4, X1, R3 instances support Enhanced Networking

**Cloud Watch**
* Minimum interval is 1 minute
* Supports all EC2 instances
* Metrics are retained for 2 weeks after an instance termination
* Archiving data can be accomplished by calling mon-get-stats from the command line and storing the results in S3 or SimpleDB
* Instance type does NOT effect CloudWatch pricing

**Auto Scaling**
* Your call on how fast you scale up or scale down
* Auto Scale CAN NOT launch more instances then your limit. Request a limit increase if needed
* Terminating an Auto Scale Group will terminate instances it created

**Elastic Load Balancer**
* Classic Load Balancer
    * Supports all EC2 instances
    * Supports HTTP, HTTPS, SSL, and TCP
    * Supports IPv4 and IPv6
    * EC2 instances CAN be configured to ONLY receive traffic from ELB
    * If your using a VPC, you can use security groups with Classic Load Balancer
    * You can map Both HTTP and HTTPS to the LB
    * Use CloudTrail to monitor API calls
    * Supports SSL termination on the LB
* Application Load Balancer
    * Supports All EC2 instances
    * Supports HTTP and HTTPS
    * HTTP/2 IS supported - clients will connect over TLS
    * Ports 1-65535 are supported
    * WebSockets are supported
    * Request Tracing is supported
    * Does NOT support EC2 Classic
    * Is NOT and will NOT be feature parity with Classic Load Balancer
    * Can be configured with a Security Group
    * EC2 instances CAN only accept traffic from Application LB
    * You CAN NOT convert a Classic LB to an Application LB or reverse
    * This is NOT a Layer 4 LB - Use a Classic LB instead
    * Use Cloud Trail to monitor API calls
    * Allows SSL termination on the LB
    * Only Encryption to a back-end server is supported - NOT authentication
    * Supports IPv6
    * Can be configured to use AWS WAF (Web Application Firewall)

**Reserved Instances**
* Provide a significant discount over On-Demand instances
* Standard RIs do NOT allow you to change instance configuration during the term.
* Convertible RIs allow you to change instance configuration during the term.
* Both allow you to reserve capacity in the AZ
* If you DON'T need capacity reservation, consider a Regional RI
* An existing Instance CAN be converted into an RI
* You CAN modify a Standard RI's AZ
* You CAN modify a Convertible RI's Instance Type, OS, tenancy, and Payment option during it's term
* RIs CAN NOT be applied to Spot Instances or Dedicated Hosts
* Volume discounts ARE available for Standard RIs
* Convertible RIs are NOT eligible for volume discounts

**Convertible Reserved Instances**
* An Instance that's attributes can be changed during it's term
* Commitment of 3 years
* IS associated with a specific Region
* CAN be exchanged for a different RI - may incur a fee
* There are NO exchange limits on a CRI

**Reserved Instance Marketplace**
* For selling RIs
* Do this through the EC2 Console
* Can sell any RI that has been active for AT LEAST 30 days from AWS receiving payment
* You can remove an RI from the Marketplace until it's sale is marked Pending
* You can choose the price
* You CAN resell an instance you bought from the Marketplace
* Must have a US Bank Account - Non US bank accounts coming soon
* Can NOT sell RIs purchased from the public volume pricing tier
* AWS charges a 12% service fee when selling
* You will NOT receive a refund for Premium Support if you had it
* You'll be notified via email once a day on the status of the sale
* You can NOT purchase your own RIs from the Marketplace
* If you ARE a premium support customer, you WILL pay premium support for instances purchased through the Marketplace

**Spot Instances**
* Allows bidding on unused EC2 capacity
* Can run the Spot Instance until the bid exceeds the current Spot Price
* T2 and HS1 are NOT available as Spot Instances
* Default limit of 20 Spot Instances per Region
* Windows Server WITH SQL Server is NOT available as a Spot Instance
* All other Linux / Unix and Windows servers ARE available
* Amazon DevPay is NOT supported with Spot Instances
* Can NOT use a Spot Instance with a Paid AMI for Third-Party Software
* IF AWS terminates the SI, you will NOT pay for the partial hour. You WILL pay for the partial hour if YOU terminate it
* A Spot Fleet is multiple Spot Instances you bid on at the same time
* No additional charge for Spot Fleets
* Spot Fleets have their own instance limits
* Spot Fleets can NOT exceed your instance limit. Request a limit increase.
* Spot Fleets are NOT guaranteed to be filled
* Does NOT support Multi-Region fleet requests
* Tagging is not supported on Spot Fleet Requests
* Can only modify the target capacity of a Spot Fleet Request
* Spot Fleets CAN be used with Auto Scaling. Can NOT be used with Load Balancing, or Map Reduce to trigger requests


