# On-Premises to AWS DataSync Architecture

This architecture shows how data can be transferred from on-premises storage to AWS using AWS DataSync.

## Data Flow

On-Premises Servers → DataSync Agent → VPN / Direct Connect → AWS DataSync → S3 / EFS / FSx

## Supported Source Examples

- NFS
- SMB
- HDFS

## AWS Destinations

- Amazon S3
- Amazon EFS
- Amazon FSx
