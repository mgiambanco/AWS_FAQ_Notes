**Redshift**

Petabyte scale data warehouse

This is for BIG Data and Data warehousing

* Redshift uses SQL via ODBC and JDBC
* Great for analyzing large amounts of data quickly
* Supports SSL, AES 256 and HSMs (Hardware Security Modules)
* Data is organized by column instead of by row
* Columnar data can be compressed more then row based data and is stored sequentially on disk
* Massively Parallel - Automatically distributes data and query load across all nodes
* A Leader Node receives queries from the client, parses the queries and develops an execution plan which are ordered steps to process these queries
    * It then coordinates with the compute nodes to process them in parallel, aggregating the intermediate results from these nodes and returning the final result back to the client
* Compute nodes can be:
    * Dense Storage
        * Provide very large data warehouses using HDDs for very low price point
        * Available in 2 sizes
            * Extra Large
                * 3 HDDs with a total of 2TB magnetic storage
            * Eight Extra Large
                * 24 HDDs with a total of 16TB magnetic storage
    * Dense Compute
        * Large
            * 160GB of SSD storage
        * Eight Extra Large
            * 2.56TB of SSD storage
* A cluster can contain 1-128 compute nodes depending on node type
* Connect to it via it's endpoint and JDBC or ODBC connection string from the AWS console
* Ideal for large volumes of structured data
* Continuously backed up to S3 for eleven 9s
* If a drive fails, you might see a slight latency while Redshift rebuilds the drive from replicas
* New nodes are automatically provisioned and begins the restore from S3
* Most frequently executed queries take top priority
* Adding or removing nodes can be done via a single API call or the Console
* Patches and upgrades are automatically applied by AWS
* Loading data can be done from S3, DynamoDB, EMR, or Data Pipeline and or any SSH via EC2 or on-premises
* Data will be attempted to be loaded in parallel to each compute node to maximize the rate at which you can ingest the data
* Data can be loaded via an SQL Insert but this may be slower then from S3 or Dynamo DB
* The AWS Copy Command can be used to load data from AWS EMR, DynamoDB or any SSH enabled host
* Use AWS Import / Export to transfer data to S3 from portable storage devices
* Use AWS Direct Connect to load data from your private network - 1Gbit / second or 10Gbit / second are available
* Data is kept encrypted both in transit and at rest
* At rest is AES 256 bit encrypted as it's written to the disk
* Redshift can be used in a VPC
* Redshift nodes are NOT accessible directly and are in a private network. You can only access the cluster's leader node
* Redshift automatically detects node failure
* If an AZ has a failure, the Redshift clusters will NOT be available until the AZ recovers
* Redshift does NOT support Multi-AZ deployments - ONLY single
    * Use a Redshift cluster in separate AZs, loading the same data from the same S3 bucket to get around this
* Data is backed up to S3
* Backups are retained for 1 day - you can configure this up to 35 days
* You have access to all of the automated backups within the backup window
* Backup is automatically configured with the 1 day retention policy. Up to you to change it to longer
* Use the Console or ModifyCluster API to change the retention period
* If you delete a cluster, the backups are deleted also. You can take a final snapshot
* Manual backups of the warehouse are retained on S3
* Scaling the cluster takes place immediately
* The existing warehouse cluster remains available for READ operations while the new cluster is created while scaling
* When the new cluster is ready, the existing cluster will be temporarily unavailable while the canonical record is updated - This usually takes just a few minutes
* Monitor Redshift via CloudWatch
* You can change the default scheduled maintenance window via the API or the Redshift Console. Updates and patches will happen during this time.
