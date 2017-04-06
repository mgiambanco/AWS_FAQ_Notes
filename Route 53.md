**Route 53**

[AWS Route 53 FAQ](https://aws.amazon.com/route53/faqs/)

DNS

* 53 is the port of DNS
* Create and Manage Public DNS records
* You can purchase domain names via Route 53
* You can transfer a domain name to Route 53
* Each zone has it's own virtual DNS servers
* Access is controlled via IAM
* Activation can take up to 24 hours
* Route 53 has a SLA
* Route 53 uses a anycast network
* Route 53 is limited to 500 hosted zones and 10,000 resources per hosted zone
* Route 53 CAN import zone files
* Route 53 DOES NOT provide website hosting
* Record Types
    * A
    * AAAA
    * CNAME
    * MX
    * NAPTR
    * NS
    * PTR
    * SOA
    * SPF
    * SRV
    * TXT
    * ALIAS
* Route 53 supports wild card entries for all record types
* Record types do NOT have a default TTL - you must specify when configuring
* You can use an Alias record type to map a sub domain (test.domain.com) to an ELB, CloudFront or S3
* Changes to a resource record is transactional. All or nothing
* DNS Changes should propagate within 60 seconds to AWS networks around the world.
* CloudTrail can monitor Route 53 changes
* DNSSEC is NOT supported by Route 53 right now
* Route 53 DOES support IPv6
* Zone Apex can point to an ELB, CloudFront, Elastic Beanstalk, and S3 via the Alias record type
* Route 53 supports Weighted Round Robin
* Route 53 supports Latency Based Routing and will route your user to the Region of lowest latency in Multi Region Applications
* Route 53 Geo DNS allows load balancing via a users geographic location
* You should still have a Global Record when using Geo DNS incase something is missed
* Use Route 53 Traffic Flow to "stack" routing policies including latency, geo, endpoint health, etc...
* A Traffic Policy defines these routes and can be applied to many DNS names
* You CAN NOT use an Alias record to point to a DNS name managed by a traffic policy
* Route 53 supports Private DNS
* Private DNS is not exposed to the internet
* Private DNS MUST be used with a VPC
* Multiple VPCs can be used with a single hosted zone in Private DNS
* VPCs belonging to different AWS accounts can be associated with Private Hosted Zones
* Private DNS is available to all Regions
* DNS Failover is available for Private DNS
* DNS Failover consists of Health Checks and Failover
* DNS Failover can be used for ELBs via an Alias record and Evaluate Target Health
* DNS Failover can failover to a backup site such as a static site on S3
* All Record Types can be used with DNS Failover EXCEPT SOA and NS records
* DNS Failover can failover to data centers NOT AWS (Rackspace, DO, Google, Azure, etc...)
* Route 53 does NOT making routing decisions based on traffic capacity of a AWS service. Only based on the traffic policy / health checks enabled
* The Health Check threshold is between 1 and 10 observations, with 3 being the default
* Route 53 will make an endpoint healthy again after 3 consecutive health checks have passed. No further action is required.
* Health Check observations are conducted every 30 seconds with the ability to change it to 10 seconds
* Health checks do NOT follow HTTP redirects
* A TTL of 60 seconds is recommended when using DNS Failover
* Health Checks can check via HTTP, HTTPS and TCP
* A Health Check will NOT validate an SSL certificate 
* HTTPS Health Checks support SNI
* A Health Check can check a web server for a specific string when Enable String Matching is enabled
* Health Check Metrics can be published to Cloud Watch
* Cloud Watch can notify you via SNS if Health Checks fail or pass
* Route 53 Health Checks can perform DNS Failover based on any metrics available from Cloud Watch
* You can notify AWS of health checks against your web servers that are NOT yours by filling in this form - https://aws.amazon.com/forms/route53-unwanted-healthchecks - Someone probably setup a health check via an IP address
* A domain name specified in a Health Check will be looked up via IPv4. If you want to use IPv6, specify the IPv6 address as your endpoint type
* List of TLDs AWS can register can be found here - https://d32ze2gidvkk54.cloudfront.net/Amazon_Route_53_Domain_Registration_Pricing_20140731.pdf
* It can take 1 to several hours to register a domain name
* Default registration length is 1 year
* Route 53 can enable privacy protection on a Domain Name
