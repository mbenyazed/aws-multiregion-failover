# AWS Multi-Region Active-Passive Failover Architecture

> A resilient, event-driven disaster-recovery blueprint designed to survive catastrophic regional failures while preserving client connectivity.

![AWS Architecture Diagram](https://raw.githubusercontent.com/mbenyazed/aws-multiregion-failover/main/architecture.png)

---

## Project Overview

As part of my transition into enterprise cloud infrastructure — and alongside my CCNA studies — I designed a resilient, event-driven **active-passive failover architecture** in AWS. This project bridges textbook networking concepts with production-grade cloud reality, translating path-redundancy and high-availability principles into a working multi-region design.

---

## Core Infrastructure Mechanisms

### 🌐 Edge Routing
Used **Amazon CloudFront Origin Groups** to route traffic away from a failing origin instantly — without waiting for DNS TTL expiration, which is too slow for real outages.

### 🔄 State Synchronization
Implemented **cross-region RDS PostgreSQL read replication** to maintain data integrity and minimize data loss during a regional outage.

### ⚙️ Automated Recovery Plane
Designed an automated promotion chain where **CloudWatch** metrics detect failure, publish to an **SNS topic**, and trigger a **Lambda function** that promotes the standby read replica to primary — no manual intervention required.

### 🛡️ Graceful User Experience
Integrated an **S3-hosted static maintenance page** to catch user traffic seamlessly during the brief database-promotion window, preventing transaction timeouts and connection errors.

---

## Tech Stack

| Layer | Service |
|---|---|
| Edge / CDN | Amazon CloudFront (Origin Groups) |
| Database | Amazon RDS for PostgreSQL (cross-region replica) |
| Monitoring | Amazon CloudWatch |
| Eventing | Amazon SNS |
| Automation | AWS Lambda |
| Static Fallback | Amazon S3 |

---

## Author

**Mamoun Benyazed** — Solutions Architecture & Enterprise Infrastructure
ASU W. P. Carey · Applied Business & Technology Solutions (Dec 2026) · CCNA Candidate
