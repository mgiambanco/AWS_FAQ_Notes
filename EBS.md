**EBS**

[Link to EBS FAQ](https://aws.amazon.com/ebs/faqs/)

Elastic Block Storage

Use this like a traditional file system

 * EBS volumes that are NOT the root volume can persist data after an EC2 instance is rebooted or terminated
 * 4 volume types available:
    * Provisioned IOPS SSD
        * bootable
    * General Purpose SSD
        * bootable
    * Throughput Optimized HDD
        * NOT bootable
    * Cold HDD
        * NOT bootable
 * EBS Standard Volumes were renamed to EBS Magnetic volumes
 * Provisioned IOPS SSD deliver within 10% of the provisioned IOPS performance 99.9% of the time
 * Provisioned IOPS SSDs can achieve single digit millisecond latency
 * Every increase in I/O size above 256KB increases linearly the resources you need to achieve the same IOPS rate
 * HDD backed volumes delivery within 10% of expected throughput 99% of the time
 * Multiple volumes can be striped together to achieve up to 65,000 IOPS over 1,750 MiB/s
 * Snapshots are only available through the EC2 API 
 * A volume does NOT need to be un-mounted to take a snapshot though it is recommended to properly detach the volume
 * Volume size should not impact how long it takes a snapshot to be created
 * Snapshots can be shared
 * EBS volumes CAN be encrypted via Managed Keys or the AWS KMS
