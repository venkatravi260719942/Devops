# Day 7: AWS ALB & NLB (Application and Network Load Balancers)

## 1. Introduction to Load Balancers

### What is a Load Balancer?
- **Load Balancers** distribute incoming application or network traffic across multiple targets, such as EC2 instances, to ensure high availability and fault tolerance.
- AWS offers several types of load balancers: **Application Load Balancer (ALB)**, **Network Load Balancer (NLB)**, and **Classic Load Balancer (CLB)** (though CLB is being phased out in favor of ALB and NLB).

---

## 2. Application Load Balancer (ALB)

### What is ALB?
- **Application Load Balancer (ALB)** operates at the **application layer** (Layer 7) of the OSI model.
- ALB is designed to handle HTTP and HTTPS traffic, providing advanced routing features based on the content of the request.

### Key Features:
- **Content-based Routing**: Routes requests based on URL path, host headers, or query parameters.
- **Host-based Routing**: Directs traffic to different target groups based on the domain name.
- **Path-based Routing**: Routes requests to different target groups based on URL path.
- **WebSocket Support**: Supports WebSocket connections for real-time, two-way communication.
- **SSL Termination**: Handles SSL/TLS termination, allowing you to offload encryption/decryption from your application.

### Use Cases:
- Microservices architectures where different services need to handle different paths or domains.
- Applications requiring advanced routing, such as sending traffic to different versions of an application for canary releases.

### How to Set Up ALB:
1. **Log in to the AWS Management Console**.
   - Navigate to the **EC2 Dashboard** and select **Load Balancers**.
   
2. **Create an ALB**.
   - Click on **Create Load Balancer** and select **Application Load Balancer**.
   - Configure the load balancer settings, including:
     - **Name**: Give your ALB a name.
     - **Scheme**: Choose between **internet-facing** or **internal**.
     - **Listeners**: Set up HTTP and/or HTTPS listeners.
     - **Availability Zones**: Select the VPC and subnets where the ALB will be deployed.
   
3. **Configure Security Settings**.
   - Set up SSL certificates for HTTPS listeners using **AWS Certificate Manager (ACM)**.

4. **Configure Routing**.
   - Define **target groups** and set up **rules** to route traffic based on URL path or host headers.

5. **Register Targets**.
   - Add EC2 instances or other targets to your target groups.

6. **Review and Create**.
   - Review all configurations and click **Create** to deploy your ALB.

---

## 3. Network Load Balancer (NLB)

### What is NLB?
- **Network Load Balancer (NLB)** operates at the **network layer** (Layer 4) of the OSI model.
- NLB is designed to handle TCP, UDP, and TLS traffic, providing high performance and low latency.

### Key Features:
- **TCP/UDP Load Balancing**: Handles both TCP and UDP traffic with low latency.
- **Static IP Addresses**: Provides a static IP address for the load balancer.
- **High Throughput**: Capable of handling millions of requests per second while maintaining low latency.
- **TLS Termination**: Supports TLS termination, offloading encryption/decryption from your instances.

### Use Cases:
- Applications requiring ultra-low latency and high throughput, such as gaming or financial applications.
- Services that require static IP addresses and high performance.

### How to Set Up NLB:
1. **Log in to the AWS Management Console**.
   - Navigate to the **EC2 Dashboard** and select **Load Balancers**.
   
2. **Create an NLB**.
   - Click on **Create Load Balancer** and select **Network Load Balancer**.
   - Configure the load balancer settings, including:
     - **Name**: Give your NLB a name.
     - **Scheme**: Choose between **internet-facing** or **internal**.
     - **Listeners**: Set up TCP, UDP, and/or TLS listeners.
     - **Availability Zones**: Select the VPC and subnets where the NLB will be deployed.
   
3. **Configure Security Settings**.
   - For TLS listeners, configure **TLS certificates** using **AWS Certificate Manager (ACM)**.

4. **Configure Routing**.
   - Define **target groups** for your load balancer.
   - Register targets (e.g., EC2 instances) with the target groups.

5. **Review and Create**.
   - Review all configurations and click **Create** to deploy your NLB.

---

## 4. Comparing ALB and NLB

### ALB vs. NLB

| Feature               | ALB                                          | NLB                                          |
|-----------------------|----------------------------------------------|----------------------------------------------|
| **Layer**             | Application Layer (Layer 7)                 | Network Layer (Layer 4)                     |
| **Protocols**         | HTTP, HTTPS                                 | TCP, UDP, TLS                               |
| **Routing**           | Content-based, host-based, path-based       | TCP/UDP, based on IP address and port       |
| **Use Case**          | Web applications, microservices, content-based routing | High-performance applications, static IP, low latency |
| **Performance**       | Optimized for web traffic and SSL termination | High throughput, low latency                |
| **IP Addresses**      | Dynamic IP addresses                        | Static IP addresses                         |

---

## 5. Best Practices for ALB and NLB

### A. ALB Best Practices:
1. **Use SSL/TLS**: Encrypt data in transit using SSL/TLS.
2. **Implement Routing Rules**: Utilize content-based routing to direct traffic to appropriate services.
3. **Monitor Performance**: Use **CloudWatch** metrics to monitor ALB performance and troubleshoot issues.

### B. NLB Best Practices:
1. **Static IP**: Use the static IP feature for services requiring a fixed IP address.
2. **Optimize Performance**: Configure target groups and listeners for optimal performance and low latency.
3. **Security**: Ensure that security groups and NACLs are properly configured to control traffic flow.

---

## Summary
Today, we explored **Application Load Balancers (ALB)** and **Network Load Balancers (NLB)**. You learned about their features, use cases, and how to set them up for different types of traffic. ALB is ideal for web applications with advanced routing needs, while NLB is suited for high-performance, low-latency applications.

**Key Takeaways:**
- **ALB** provides advanced content-based routing for HTTP/HTTPS traffic.
- **NLB** delivers high performance and low latency for TCP/UDP traffic.
- Both types of load balancers help distribute traffic and ensure high availability.

---

### Next Session
In the next session, we will cover **ECS**

---

**Thank you!**
