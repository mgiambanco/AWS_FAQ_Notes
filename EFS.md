**EFS**

[AWS EFS FAQ](https://aws.amazon.com/efs/faq/)

Scalable block file storage

* Compatible with all EC2 instances
* Load data from an EC2 instance or on-premise datacenter servers
* Can be mounted to an EC2 instance
* Can be mounted to on-premise server via On-Premises Access
* File system is redundantly stored across multiple AZs
* Can be accessed concurrently from Multiple AZs in a given Region
* Use standard 3rd party backup tools to backup
* Can use AWS Data Pipeline to create automated copies based on a schedule
* Can Store Petabytes of data
* Automatically grows and shrinks with files
* Can create up to 10 file systems per Region. Use http://docs.aws.amazon.com/general/latest/gr/aws_service_limits.html to request a limit increase
* General Purpose performance mode is the default
* Max I/O performance mode is for applications with 10s, 100s or 1000s of EC2 instances accessing it
* Throughput scales as the file system grows
* Allows bursting - baseline of 50MB/s per TB, can burst to 100MB/s
* File systems larger then 1TB can burst to 100MB/s per TB
* Access is controlled via IAM
* Does NOT currently provide encryption on data at rest - may be coming soon
* On-Premise access is available via AWS Direct Connect
* Follow standard Linux mounting command to mount the EFS
* EFS is NOT available over AWS VPN
* Concurrent access is available via On-Premise and via an EC2 instance
* There can be latency over Direct Connect in the tens of milliseconds
* Can use CloudWatch to monitor and report
* Metadata Tagging is available
* Has an automatically generated ID - Tag the name for easier identification
