
# TaskFlow Cloud — AWS Architecture

## Architecture Diagram

```mermaid
flowchart TB
    U[User / Browser]
    R53[Amazon Route 53]
    CF[Amazon CloudFront]
    S3[Amazon S3 - Static Frontend]
    ALB[Application Load Balancer]

    subgraph VPC["Amazon VPC"]
        subgraph AZ1["Availability Zone 1"]
            EC2A[EC2 App Instance A]
        end
        subgraph AZ2["Availability Zone 2"]
            EC2B[EC2 App Instance B]
        end
        ASG[EC2 Auto Scaling]
        RDS[Amazon RDS Multi-AZ]
    end

    IAM[AWS IAM]
    KMS[AWS KMS Encryption]
    CW[Amazon CloudWatch]

    U --> R53
    R53 --> CF
    CF --> S3
    U --> ALB
    ALB --> EC2A
    ALB --> EC2B
    ASG -. manages .-> EC2A
    ASG -. manages .-> EC2B
    EC2A --> RDS
    EC2B --> RDS
    IAM -. access control .-> EC2A
    IAM -. access control .-> S3
    KMS -. encryption keys .-> RDS
    CW -. monitoring .-> EC2A
    CW -. monitoring .-> EC2B
```

## Component Responsibilities

| AWS Service | Purpose |
|---|---|
| Route 53 | Routes domain requests |
| CloudFront | Delivers frontend content |
| S3 | Stores static frontend files |
| Application Load Balancer | Distributes application requests |
| EC2 Auto Scaling | Maintains the desired number of instances |
| Amazon VPC | Isolates the cloud network |
| RDS Multi-AZ | Provides relational database availability |
| IAM | Controls permissions |
| KMS | Manages encryption keys |
| CloudWatch | Collects metrics, logs, and alarms |

## Security and Availability

- Use public subnets only for resources that require public access.
- Keep application instances and the database in appropriately restricted subnets.
- Use HTTPS/TLS for data in transit.
- Use IAM least-privilege policies.
- Enable supported encryption at rest.
- Deploy application instances across two Availability Zones.
- Test failover, access controls, and recovery before claiming production readiness.

## Implementation Status

This is a proposed reference architecture for the TaskFlow Cloud capstone. The frontend demonstration runs on CodePen. The AWS infrastructure shown above has not been deployed or tested.
