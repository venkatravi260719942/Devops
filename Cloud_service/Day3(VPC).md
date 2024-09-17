# Day 3: AWS VPC (Virtual Private Cloud)

## 1. Introduction to VPC

### What is VPC?
- **Amazon Virtual Private Cloud (VPC)** is a service that allows you to create and control a virtual network in AWS.
- You can define your own IP address ranges, subnets, route tables, and network gateways.
- **Why VPC?** VPC helps isolate resources for security and network control, ensuring they are only accessible in desired ways.

### Key Concepts:
- **CIDR Block**: The range of IP addresses for the VPC.
- **Subnets**: Divide the VPC into smaller networks.
- **Route Tables**: Define the routing rules within the VPC.
- **Internet Gateway**: Connect your VPC to the internet.
- **NAT Gateway**: Allows instances in private subnets to access the internet.
- **Security Groups & NACLs (Network Access Control Lists)**: Control traffic flow in and out of resources.

---

## 2. Creating a VPC

### Steps to Create a VPC:
1. **Log in to the AWS Management Console**.
   - Navigate to the **VPC** service.

2. **Create a VPC**.
   - Click on **"Your VPCs"** in the left menu and then **"Create VPC"**.
   - Set the following:
     - **VPC Name**: Name your VPC (e.g., `MyFirstVPC`).
     - **IPv4 CIDR Block**: Define your IP range, such as `10.0.0.0/16`.

3. **Add Subnets**.
   - Subnets can be created in specific Availability Zones.
   - Types of subnets:
     - **Public Subnet**: Direct access to the internet.
     - **Private Subnet**: No direct internet access (secured by NAT Gateway).

4. **Attach an Internet Gateway**.
   - Create and attach an **Internet Gateway (IGW)** to the VPC to enable internet access.

5. **Set Up Route Tables**.
   - Create a **Route Table**.
   - Add a route for internet traffic (`0.0.0.0/0`) to go through the **Internet Gateway** for the public subnet.

---

## 3. VPC Components and Configuration

### A. Subnets
- A **subnet** is a range of IP addresses within your VPC.
  - **Public Subnets** are for resources that need direct access to the internet (e.g., web servers).
  - **Private Subnets** are for internal resources (e.g., databases).
  - You can have multiple subnets in different Availability Zones.

### B. Internet Gateway (IGW)
- An **Internet Gateway** allows instances in your VPC to communicate with the internet.
  - It must be attached to your VPC to route internet-bound traffic.

### C. NAT Gateway
- A **NAT Gateway** allows instances in **private subnets** to access the internet for updates and patches without exposing them directly.
  - It provides outbound internet access but no inbound access from the internet.

### D. Route Tables
- **Route Tables** define where network traffic is directed.
  - You can have different route tables for public and private subnets.
  - Routes include destination (`0.0.0.0/0` for all internet-bound traffic) and target (e.g., Internet Gateway or NAT Gateway).

### E. Security Groups and Network ACLs (NACLs)
- **Security Groups** act as a firewall at the instance level.
  - You can allow or block specific inbound and outbound traffic (e.g., HTTP, SSH).
- **Network ACLs** (NACLs) control traffic at the subnet level.
  - They provide an extra layer of security for your subnets.

---

## 4. Connecting VPCs

### A. VPC Peering
- **VPC Peering** allows communication between two VPCs (even across different AWS accounts) over a private network.
  - It’s useful when you want two VPCs to share resources (e.g., databases, web servers).

### B. VPN Gateway
- **Virtual Private Gateway** allows you to create a secure, encrypted connection between your on-premises data center and your AWS VPC.
  - This is useful for hybrid cloud architectures.

---

## 5. Use Cases for VPC

### A. Hosting a Web Application
- A typical setup involves:
  - **Public Subnet**: For web servers (EC2 instances) that need internet access.
  - **Private Subnet**: For databases (RDS) that should not be exposed to the internet.
  - **Security Groups**: Control access to the instances (allow HTTP/HTTPS traffic for web servers, block external access to the database).

### B. Isolating Environments
- Use separate VPCs to isolate development, staging, and production environments for security and to avoid resource conflicts.

### C. Hybrid Cloud
- Use a **VPN Gateway** or **AWS Direct Connect** to securely connect on-premises data centers to your AWS VPC.
  - This can extend your local infrastructure into the cloud.

---

## 6. Best Practices for VPC

1. **Use Multiple Subnets**: Separate public and private resources for better security and scalability.
2. **Use Security Groups and NACLs**: Apply security rules at both the instance and subnet levels for defense in depth.
3. **Regular Backups**: Regularly back up route tables, security group rules, and VPC configurations.
4. **Monitor Traffic**: Use **VPC Flow Logs** to monitor and troubleshoot network traffic in your VPC.

---

## Summary
Today, we explored **Amazon VPC**, which allows you to define and control your network within AWS. You learned how to create a VPC, configure subnets, route tables, and gateways, and apply best practices for securing and scaling your infrastructure.

**Key Takeaways:**
- VPC is a foundational service for creating isolated networks in AWS.
- Subnets allow you to segment your resources into public and private groups.
- Route tables and gateways (IGW, NAT) handle traffic routing and security.
- VPC Peering and VPNs extend networking capabilities across VPCs or into on-premises environments.

---

### Next Session
In the next session, we will cover **Route 53** to learn about domain management and DNS routing in AWS.

---

**Thank you!**
