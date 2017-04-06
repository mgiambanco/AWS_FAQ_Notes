RDS
Relational Database Service

* Supports MySQL, MariaDB, Oracle, SQL Server, PostgreSQL
* AWS Manages servers; patches; infrastructure
* Up to 40 RDS DB Instances
    * Up to 10 can be Oracle or SQL
    * All 40 can be used for Aurora, MySQL, MariaDB, PostgreSQL
* Aurora, MySQL, MariaDB, PostgreSQL can have unlimited databases
* Oracle can have 1 database per instance
* SQL server can have 30 databases per instance
* Import via usual import means; mysqlimport, import / export sql, etc...
* Maintenance can last up to 30 minutes and you can tell AWS when to do this
* Running RDS in Multi AZ can reduce this impact
* Enhanced Monitoring provides access to over 50 CPU, memory, file system and disk IO metrics
* MySQL and MariaDB allow access to slow query log files
* AWS aims to support new DB engine versions within 5 months of their general availability
* Not all DB versions are available in all regions
* Scheduled upgrades will be announced via email at least 30 days in advance
* Major version upgrades can have compatibility risk and upgrades must be initiated by you
* RDS can have reserved instances
    * Payment options are No Upfront, Partial Upfront and All Upfront
    * You can purchase up to 40 reserved instances - fill out https://aws.amazon.com/contact-us/request-to-increase-the-amazon-rds-db-instance-limit/ to request more
    * Existing DB instances CAN be converted into reserved instance
    * Reserved instances CAN NOT be moved between regions but CAN be moved between AZs in the sam Region
    * Read Replicas CAN be reserved
* RDS uses EBS volumes for database and log storing
* MySQL and Oracle may see performance improvements by scaling up storage
* SQL Server CAN NOT scale up storage
* Backups are Point-In-Time recovery
* When automated backups are turned on, full daily snapshots are automatically taken
* You can initiate a DB snapshot at anytime, how often as you'd like
* Automated backups are enabled by default and have a 1 day retention period.
* You can choose the preferred backup window time
* Backups are stored in S3
* Automated backups are deleted when the DB instance is deleted. 
* Manual DB snapshots are retained if the DB instance is deleted
* During failover, the DB instance IP can change - use the DNS Name of the instance instead
* A DB Instance CAN NOT be move from inside a VPC to outside a VPC
* If the DB instance is NOT in a VPC, it CAN be moved into a VPC
* DB Subnet Groups CAN be updated to add more subnets.
* MySQL, MariaDB, SQL Server, PostgreSQL and Oracle can use encrypted (SSL) connections
* All DBs support encryption at rest using AWS KMS
* Encryption CAN be added to previously unencrypted DBs
* MySQL, MariaDB, PostgreSQL and Aurora support Read Replicas
* Read Replicas are NOT designed to improve write availability
* Multi-AZ and Read Replicas can be used together
* When Multi-AZ is turned on, RDS will automatically create another DB instance in another AZ
* If 1 instance goes down, RDS will failover to the next available instance
* As the DNS does not change when this happens, use the DNS Name when connecting to the DB. NOT THE IP
* The standby instance is JUST a standby - the primary will be used in all reads and writes
* You MAY experience latency in a Multi-AZ config as the DB needs to SYNCHRONOUSLY replicate the data
* If failover occurs, RDS will emit a DB Instance Event.
* Failover should only take 1 to 2 minutes but can be longer if uncommitted transactions are outstanding
* You can force a failover by rebooting the instance
* Standbys exist in a different AZ but in the same Region
* In Multi-AZ, DB Snapshots are taken from the primary DB instance and may cause latency while the snapshot is taken
* Automatic backups MUST be enabled for Read Replicas to work
* MySQL, PostgreSQL and MariaDB support Read Replicas
* MySQL, MariaDB and PostgreSQL support up to 5 Read Replicas for a given DB instance
* Read Replicas are ASYNCHRONOUS 
* Read Replicas DO NOT enhance write availability
* If a Multi-AZ failover occurs, Read Replicas will resume replication once failover has finished
* If a Read Replica becomes inconsistent, delete it and create a new one
* Read Replicas should have >= compute and storage resources as their DB instance
* Enhanced monitoring supports all RDS engines
* Enhanced monitoring supports all instance types EXCEPT t1.micro and t1.small
* Metrics can be viewed from 1 second to 1 hour ago via the RDS console
* RDS Enhanced Metrics are delivered to Cloud Watch
* Enhanced Monitoring outputs JSON - 3rd party tools can access this data via Cloud Watch Log Subscriptions
