# Day 6: AWS EBS (Elastic Block Store) and EFS (Elastic File System)

## 1. Introduction to EBS (Elastic Block Store)

### What is EBS?
- **Amazon EBS (Elastic Block Store)** provides persistent block storage volumes for use with Amazon EC2 instances.
- EBS volumes are used as the primary storage for data that needs to be accessed frequently, such as operating systems, applications, and databases.

### Key Concepts:
- **Block Storage**: Storage that provides raw storage volumes for use with EC2 instances. Each volume is a block device.
- **Volume Types**: Different types of EBS volumes are optimized for various use cases:
  - **General Purpose (SSD)**: Balanced price and performance (e.g., `gp3`).
  - **Provisioned IOPS (SSD)**: High performance for I/O-intensive applications (e.g., `io1`).
  - **Throughput Optimized (HDD)**: Low-cost storage for frequently accessed data (e.g., `st1`).
  - **Cold HDD**: Low-cost storage for infrequently accessed data (e.g., `sc1`).

---

## 2. Creating and Managing EBS Volumes

### A. Creating an EBS Volume:
1. **Log in to the AWS Management Console**.
   - Navigate to the **EC2 Dashboard**.
   - Click on **Volumes** under the **Elastic Block Store** section.

2. **Create a Volume**.
   - Click on **Create Volume**.
   - Choose the volume type and size (e.g., `100 GB`, `gp3` type).
   - Select the Availability Zone to match your EC2 instance.

3. **Attach the Volume to an EC2 Instance**.
   - Select the volume and click **Actions** > **Attach Volume**.
   - Choose the EC2 instance you want to attach it to.
   - Specify the device name (e.g., `/dev/sdf`).

4. **Format and Mount the Volume** (Linux):
   - Connect to your EC2 instance using SSH.
   - Format the volume (e.g., `sudo mkfs -t ext4 /dev/xvdf`).
   - Mount the volume (e.g., `sudo mount /dev/xvdf /mnt/mydata`).

### B. Managing EBS Volumes:
- **Snapshot**: Create snapshots for backup and disaster recovery.
  - Go to **Snapshots** in the EC2 Dashboard, click **Create Snapshot**.
  - Snapshots are incremental and stored in S3.
- **Volume Encryption**: Encrypt EBS volumes for data security using AWS Key Management Service (KMS).
  - Enable encryption when creating a new volume.

---

## 3. Introduction to EFS (Elastic File System)

### What is EFS?
- **Amazon EFS (Elastic File System)** provides a fully managed, scalable file storage system for use with Amazon EC2 instances.
- EFS is ideal for applications that require a file system interface and shared access to data.

### Key Concepts:
- **File Storage**: File-level storage that can be mounted on multiple EC2 instances simultaneously.
- **Performance Modes**:
  - **General Purpose**: For latency-sensitive applications.
  - **Max I/O**: For applications requiring higher throughput and IOPS.
- **Throughput Modes**:
  - **Bursting**: Scales throughput up and down based on activity.
  - **Provisioned**: Allows you to specify a fixed throughput rate.

---

## 4. Creating and Managing EFS

### A. Creating an EFS File System:
1. **Log in to the AWS Management Console**.
   - Navigate to the **EFS Dashboard**.

2. **Create a File System**.
   - Click on **Create file system**.
   - Choose the performance and throughput modes.
   - Configure **VPC** settings and **mount targets** in your VPC subnets.

3. **Mount the File System**:
   - Install the **NFS client** on your EC2 instance (e.g., `sudo yum install -y nfs-utils` on Amazon Linux).
   - Mount the file system using the mount target DNS name (e.g., `sudo mount -t nfs -o tls <file-system-id>.efs.<region>.amazonaws.com:/ /mnt/efs`).

### B. Managing EFS:
- **Access Control**: Use **Network ACLs** and **Security Groups** to control access to your EFS file system.
- **Scaling**: EFS automatically scales up and down based on the data stored.
- **Backups**: Use **AWS Backup** to create automated backups of your EFS file system.

---

## 5. EBS vs. EFS

### A. EBS (Elastic Block Store)
- **Use Case**: Ideal for single EC2 instances needing persistent block storage.
- **Access**: Mounts directly to a single EC2 instance.
- **Performance**: High performance with various volume types.
- **Cost**: Charged based on provisioned storage and IOPS.

### B. EFS (Elastic File System)
- **Use Case**: Suitable for applications requiring a shared file system accessed by multiple EC2 instances.
- **Access**: Can be mounted on multiple EC2 instances simultaneously.
- **Performance**: Scales with storage and supports high throughput and IOPS.
- **Cost**: Charged based on the amount of data stored and throughput provisioned.

---

## 6. Best Practices for EBS and EFS

### A. EBS Best Practices:
1. **Regular Snapshots**: Take regular snapshots to back up data.
2. **Monitor Performance**: Use CloudWatch to monitor volume performance and IOPS.
3. **Secure Data**: Encrypt volumes and use secure access methods.

### B. EFS Best Practices:
1. **Access Control**: Use security groups and NACLs to control access to the file system.
2. **Monitor and Scale**: Monitor performance and adjust throughput settings as needed.
3. **Backups**: Use automated backups to protect data.

---

## Summary
Today, we explored **Amazon EBS** and **Amazon EFS**. You learned about EBS volumes, how to create and manage them, and the differences between EBS and EFS. EBS provides block storage for single EC2 instances, while EFS offers scalable file storage accessible by multiple instances.

**Key Takeaways:**
- **EBS** is ideal for persistent block storage with high performance and customization.
- **EFS** provides scalable file storage with shared access for multiple EC2 instances.
- Both services are integral to managing data storage in AWS and have specific use cases and best practices.

---

### Next Session
In the next session, we will cover **AWS Artifact** to understand how to manage compliance reports and other security documents in AWS.

---

**Thank you!**
