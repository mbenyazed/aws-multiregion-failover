Project Overview:
As part of my transition into enterprise cloud infrastructure and my CCNA studies, I designed a resilient, event-driven active-passive failover architecture in AWS. This project bridges textbook networking concepts with production-grade cloud reality.

Core Infrastructure Mechanisms:
Edge Routing: Utilized Amazon CloudFront Origin Groups to route traffic away from failing origins without waiting for DNS TTL expirations.

State Synchronization: Implemented cross-region RDS PostgreSQL replication to maintain data integrity during a regional outage.

Automated Recovery Plane: Designed an automated promotion chain using CloudWatch latency metrics to trigger an SNS topic, which executes a Lambda function to promote the read replica without manual intervention.

User Experience: Integrated an S3-hosted static maintenance page to catch user traffic seamlessly during the database promotion window.
