# DynamoDB

- what is dynamoDB
- Why Used
- For which application its suitable
- Amazon DynamoDB Accelerator DAX caching
- keys - local, global
- streams
- joins - modelling
- scan, query
- How to connect with nodejs
- lambda function trigger
- file dump in db - import export both

# What is DynamoDB?

# What are NoSQL databases?
  NoSQL or non-relational databases focus on different data storing models rather than a tabular structure. There are four types of NoSQL databases:
  
    Key-value stores
    Document stores
    Graph store
    Colum stores

DynamoDB supports both document and key-value structures.

# What are the key features of DynamoDB?
  Highly Scalable without any intervention from the user.
  It has a latency of microseconds.
  Serverless and enterprise-ready.
  Encryption at Rest.
  On-demand backup and restore.
  Point-in-time recovery.

# What are the advantages of using DynamoDB?
  We can store any amount of data with the unlimited storage provided by the DynamoDB service.
  The data we store replicates over many availability regions. It allows to easily cope with global-scale applications and make sensitive information highly available.
  It is highly cost-effective, and the users have to pay only for what they use.
  Easy administration and the user doesn't have to worry about software patching, setup, and configuration because AWS fully manages DynamoDB.
  DynamoDB has an advanced system for reporting and highly secured user authentication mechanisms to provide maximum security over sensitive data.

 # What are the disadvantages of DynamoDB?
  No triggers and lack server-side scripts.
  No table joins possible.
  Data querying is highly limited.
  The cost can be unpredictable with spikes in usage.

  # What are the DynamoDB pricing tiers? 
    
    On-demand capacity mode: This pricing tier focuses on the incoming traffic to the application and scales the database instance based on that. This pricing tier is ideal when the traffic is not predictable.
    Provisioned capacity mode: This pricing tier lets users specify the reads and writes per second or choose auto-scaling. This option works best when the traffic is consistent and predictable.

# DynamoDB Cost Optimization - Best Practices

Because Amazon DynamoDB is a fully managed database where a user does not provision any machines, the pricing is not as straight forward

1. Use cheaper regions
If you are not concerned about your data's location because you don't need to meet any regulations or compliance standards, you can provision your tables in regions where it's cheaper. For example, if your table will have 100GB of data, the storage will cost $28.50 per month in Tokyo (ap-northeast-1), $29.72 per month in London (eu-west-2), or even $37.50 per month in Sao Paulo (sa-east-1).

The cheapest regions are us-east-1, us-east-2 and us-west-2 costing $0.25 per GB/month, $0.00065 per WCU/hour and $0.00013 per RCU/hour.

2. Use shorter attribute names
Because DynamoDB in both On-Demand and Provisioned capacity mode uses size-dependent billing units (1 WCU/WRU = 1KB, 1 RCU/RRU = 4KB), plus, you're paying for storage too, you should always aim to make your records as small as possible. If making attribute values is not an option, try making attribute names shorter. This helps you reduce the amount of storage required for your data. Moreover, when storing dates, you can choose the epoch time format instead of ISO dates because it's shorter too. It also makes your items compatible with DynamoDB's TTL feature.

3. Be aware of huge blobs
Saving images in DynamoDB can quickly skyrocket costs. It's very inefficient, and you should rather store all images or linked assets in S3 and save the URL pointing to it in DDB. If that's not an option, consider using compression algorithms like gzip to make blobs smaller before saving them.

4. Prefer queries over scans
DynamoDB has two ways of fetching a set of records from it: Query and Scan. While the query is using partition and sort key to get the desired piece of data fast and directly, the scan, on the other hand, is "scanning" through your whole table. The difference here is that while in Query, you are charged only for items which are returned, in scan case, you're being charged for all the rows scanned, not the total amount of items returned

# What is the maximum item size in Amazon DynamoDB?
400KB - Including both the attribute name length and the value lengths in binary format, 400KB is the maximum item size.

# What is DynamoDB Accelerator?
DAX (Amazon DynamoDB Accelerator) is a type of in-memory cache. Even when it is millions of requests per second, DynamoDB Accelerator provides a performance up to 10 times the original rate. In addition, it is fully managed and is highly available.






need to check
https://haithai91.medium.com/dynamodb-core-concept-interview-challenge-c896864799b1

    
