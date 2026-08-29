# AWS CLI Commands – EC2 and EBS

## AWS CLI Configuration

Check AWS CLI version:

```bash
aws --version
```

Configure AWS CLI:

```bash
aws configure
```

---

## EC2 Operations

### 1. Create EC2 Instance

```bash
aws ec2 run-instances \
  --image-id <ami-id> \
  --count 1 \
  --instance-type t2.micro \
  --key-name <key-name> \
  --security-group-ids <security-group-id> \
  --subnet-id <subnet-id>
```

### 2. Start EC2

```bash
aws ec2 start-instances \
  --instance-ids <instance-id>
```

### 3. Stop EC2

```bash
aws ec2 stop-instances \
  --instance-ids <instance-id>
```

### 4. Terminate EC2

```bash
aws ec2 terminate-instances \
  --instance-ids <instance-id>
```

### 5. Create EC2 Tag

```bash
aws ec2 create-tags \
  --resources <instance-id> \
  --tags Key=Name,Value=CLIDemo
```

---

## EBS Operations

### 6. Describe EBS Volumes

```bash
aws ec2 describe-volumes
```

### 7. Create EBS Volume

```bash
aws ec2 create-volume \
  --size 10 \
  --region ap-south-1 \
  --availability-zone ap-south-1a \
  --volume-type gp2
```

### 8. Attach EBS Volume

```bash
aws ec2 attach-volume \
  --volume-id <volume-id> \
  --instance-id <instance-id> \
  --device /dev/sdh
```

### 9. Detach EBS Volume

```bash
aws ec2 detach-volume \
  --volume-id <volume-id>
```

### 10. Delete EBS Volume

```bash
aws ec2 delete-volume \
  --volume-id <volume-id>
```

---

## IAM Role

IAM Roles provide secure, temporary permissions to AWS resources.

```text
EC2 Instance
      |
      v
   IAM Role
      |
      v
Temporary Credentials
      |
      v
   AWS Services
```

For production environments, follow the principle of least privilege.

---

## Important Notes

- Stop an EC2 instance when it is not required.
- Terminate an EC2 instance when it is permanently no longer required.
- Detach an EBS volume before deleting it when necessary.
- Never publish AWS Access Keys or Secret Access Keys in GitHub.
- Use IAM Roles wherever possible for AWS workloads.
