# Day 2: Topic Introduction (5 minutes)
- Explain the agenda of the day.
  - “Today, we’ll be covering EC2 storage options (EBS, Instance Store), different pricing models, security features, and management tools like Auto Scaling and Elastic Load Balancing.”

## 1. Main Lecture: Deep Dive into EC2 Features (40-50 minutes)

### A. EC2 Storage Options
- **Elastic Block Store (EBS):**
  - Explain what EBS is.
    - “EBS is durable, block-level storage that you can attach to your EC2 instances. It’s like a hard drive for your server.”
  - Discuss the different EBS volume types:
    - **General Purpose SSD (gp3, gp2):** Used for general workloads.
    - **Provisioned IOPS SSD (io2, io1):** High-performance SSD for workloads that require high I/O.
    - **Cold HDD (sc1):** Low-cost storage for infrequent access.
    - **Throughput Optimized HDD (st1):** For frequently accessed data but at a lower cost than SSD.
  - Show how to create and attach EBS volumes to EC2 instances.

- **Instance Store:**
  - Explain what instance store is.
    - “Instance store provides temporary storage that is physically attached to the host machine. It’s fast but non-persistent, meaning data will be lost if the instance is stopped or terminated.”
  - Mention when it’s useful (e.g., for caches, buffers).

### B. EC2 Pricing Models
- **On-Demand Instances:**
  - Explain that these are pay-as-you-go instances.
  - “You only pay for what you use with no long-term commitments. This is great for unpredictable workloads.”

- **Reserved Instances:**
  - Discuss how this model offers significant discounts if you commit to using instances for 1 or 3 years.
  - “Reserved Instances are useful when you have steady-state workloads and want to save costs.”

- **Spot Instances:**
  - Explain Spot Instances and how they can save up to 90% of costs but can be interrupted by AWS.
  - “Spot Instances are ideal for workloads that can handle interruptions, like batch processing and big data analytics.”

- **Savings Plans:**
  - Mention the flexible pricing option with Savings Plans, which allows discounts based on consistent usage over time, covering EC2 and other services.

### C. EC2 Security
- **Security Groups:**
  - Reiterate the importance of security groups.
  - “Security groups act as a firewall for your EC2 instances, controlling inbound and outbound traffic.”
  - Walk through creating a security group and setting rules to allow SSH or HTTP/HTTPS traffic.

- **Key Pairs:**
  - Explain how key pairs are used for secure login.
  - “To access your EC2 instance, you’ll need a key pair, which consists of a public key (kept by AWS) and a private key (kept by you). Never lose your private key!”
  
- **IAM Roles for EC2:**
  - Introduce IAM roles.
  - “IAM roles can be attached to EC2 instances to provide permissions without needing to hard-code credentials, which is much more secure.”

### D. Managing EC2 Instances
- **Auto Scaling:**
  - Explain how Auto Scaling works to automatically adjust the number of instances based on traffic or demand.
  - “With Auto Scaling, your application can scale up when demand increases and scale down when demand decreases, helping to optimize costs.”
  - Show a simple Auto Scaling configuration with thresholds for scaling.

- **Elastic Load Balancing (ELB):**
  - Discuss how ELB distributes incoming traffic across multiple EC2 instances.
  - “ELB ensures high availability and fault tolerance by spreading the traffic load across healthy instances.”
  - Introduce the different types of Load Balancers (ALB for HTTP/HTTPS traffic, NLB for low-latency TCP/UDP traffic).

## 4. Interactive Q&A (10-15 minutes)
# Top 10 EC2 Interview Questions

### 1. What is Amazon EC2, and what are its key features?
**Answer**:  
Amazon EC2 (Elastic Compute Cloud) is a web service that provides resizable compute capacity in the cloud. Key features include:
- Scalable virtual servers (instances)
- Various instance types based on CPU, memory, and storage
- Elastic IPs
- Support for multiple OS (Linux, Windows)
- Auto-scaling and load balancing
- Pricing models: On-Demand, Reserved, Spot, and Dedicated Hosts

---

### 2. What are the different types of EC2 instances?
**Answer**:  
EC2 instances are categorized based on use cases:
- **General Purpose** (e.g., t2, t3, m5): Balanced CPU and memory
- **Compute Optimized** (e.g., c5, c6g): For high-performance computing tasks
- **Memory Optimized** (e.g., r5, x1e): For RAM-intensive applications
- **Storage Optimized** (e.g., i3, d2): High IOPS and data throughput
- **Accelerated Computing** (e.g., p3, f1): For GPU or FPGA workloads

---

### 3. What are Amazon EC2 pricing models, and when should you use each?
**Answer**:  
- **On-Demand Instances**: Pay for compute capacity by the hour; ideal for short-term workloads.
- **Reserved Instances**: Significant discounts in exchange for a commitment (1 or 3 years); suitable for long-term workloads.
- **Spot Instances**: Bid for unused EC2 capacity at lower rates; ideal for fault-tolerant, flexible workloads.
- **Dedicated Hosts**: Physical servers dedicated to your use, suitable for regulatory or licensing requirements.

---

### 4. What is an AMI, and how is it different from an instance?
**Answer**:  
- An **AMI** (Amazon Machine Image) is a template for creating instances that includes the operating system, application server, and applications.
- An **instance** is a running virtual machine created from an AMI. AMIs are reusable and can be shared across accounts or regions.

---

### 5. Explain Elastic IP and how it differs from a regular IP.
**Answer**:  
An **Elastic IP** is a static, public IP address you can associate with an instance. It allows you to mask instance failures by remapping the IP to another instance.  
A **regular public IP** changes every time you stop and start the instance, while an Elastic IP is persistent until released.

---

### 6. What are security groups, and how do they differ from network ACLs?
**Answer**:  
- **Security Groups**: Act as a virtual firewall for instances to control inbound and outbound traffic. Rules are stateful (i.e., if you allow inbound, the outbound is automatically allowed).
- **Network ACLs**: Operate at the subnet level and control traffic at the network layer. Rules are stateless, meaning you need to explicitly allow both inbound and outbound traffic.

---

### 7. What is the difference between stopping and terminating an EC2 instance?
**Answer**:  
- **Stopping**: Halts the instance, retains the instance configuration and attached EBS volumes. You can restart it later.
- **Terminating**: Permanently deletes the instance and attached storage (if not configured to persist). The instance can’t be restarted after termination.

---

### 8. How does EBS (Elastic Block Store) differ from Instance Store?
**Answer**:  
- **EBS**: Persistent storage, meaning data is retained even after the instance is stopped or terminated (if configured).
- **Instance Store**: Temporary storage, meaning data is lost when the instance stops or terminates. Ideal for ephemeral data or temporary workloads.

---

### 9. What is Auto Scaling, and how does it work in EC2?
**Answer**:  
**Auto Scaling** automatically adjusts the number of EC2 instances in a group based on demand. It can scale up or down based on specified conditions like CPU utilization or request count.  
It ensures that applications have the right amount of capacity to handle traffic and improve fault tolerance and availability.

---

### 10. What is EC2 user data, and how is it used?
**Answer**:  
**User data** is a script that runs automatically when an EC2 instance is launched. It’s commonly used for bootstrapping instances, such as installing software, updates, or configuring services.  
It can be provided as a shell script or a cloud-init configuration file.


## 5. Recap & Closing (5-10 minutes)
- Summarize the key points of today’s lesson.
  - “Today, we explored EC2 storage options, including EBS and Instance Store, and discussed various pricing models like On-Demand, Reserved, and Spot Instances. We also covered how to secure and manage your EC2 instances effectively.”
  
- Set expectations for the next class.
  - “In the next session, we’ll move on to VPC, where you’ll learn how to create isolated networks in AWS. Thank you for your attention today!”
  
- Conclude the session.
  - “Thank you all! If you have any questions after the class, feel free to reach out. See you next time!”
