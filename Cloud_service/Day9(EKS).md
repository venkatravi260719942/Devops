# Day 9: AWS EKS (Elastic Kubernetes Service)

## 1. Introduction to EKS (Elastic Kubernetes Service)

### What is EKS?
- **Amazon EKS (Elastic Kubernetes Service)** is a fully managed service that simplifies running Kubernetes clusters on AWS without needing to install and operate your own Kubernetes control plane.
- EKS provides a highly available and scalable Kubernetes control plane and integrates with other AWS services for networking, security, and monitoring.

### Key Concepts:
- **Kubernetes Cluster**: A group of nodes that run containerized applications.
- **Control Plane**: Manages the Kubernetes API server, etcd database, and scheduler.
- **Worker Nodes**: EC2 instances or Fargate tasks where Kubernetes pods run.

---

## 2. Setting Up EKS

### A. Creating an EKS Cluster
1. **Log in to the AWS Management Console**.
   - Navigate to the **EKS Dashboard**.

2. **Create a Cluster**.
   - Click on **Create cluster**.
   - Enter a **Name** for your cluster and select the **Kubernetes version**.

3. **Configure Cluster Settings**.
   - **VPC**: Choose the VPC and subnets for the cluster.
   - **Cluster Security Group**: Select a security group for the cluster.
   - **IAM Role**: Attach an IAM role with the necessary permissions.

4. **Create the Cluster**.
   - Review the configuration and click **Create**. The cluster creation process may take several minutes.

### B. Configuring kubectl
1. **Install kubectl**:
   - Follow the [official kubectl installation guide](https://kubernetes.io/docs/tasks/tools/install-kubectl/) to install the Kubernetes command-line tool.

2. **Update kubeconfig**:
   - Use the `aws eks update-kubeconfig` command to configure kubectl with your EKS cluster.
     ```bash
     aws eks update-kubeconfig --name <cluster_name> --region <region>
     ```

3. **Verify Configuration**:
   - Run `kubectl get nodes` to ensure kubectl is configured correctly and can communicate with your EKS cluster.

---

## 3. Deploying Applications on EKS

### A. Creating a Deployment
1. **Prepare a Deployment YAML**:
   - Create a YAML file to define the deployment, including the container image, replicas, and resource requests/limits.
   - Example `deployment.yaml`:
     ```yaml
     apiVersion: apps/v1
     kind: Deployment
     metadata:
       name: my-app
     spec:
       replicas: 3
       selector:
         matchLabels:
           app: my-app
       template:
         metadata:
           labels:
             app: my-app
         spec:
           containers:
           - name: my-app
             image: my-app-image:latest
             ports:
             - containerPort: 80
     ```

2. **Apply the Deployment**:
   - Use `kubectl apply -f deployment.yaml` to deploy the application.

### B. Exposing the Application
1. **Create a Service**:
   - Define a service to expose the deployment.
   - Example `service.yaml`:
     ```yaml
     apiVersion: v1
     kind: Service
     metadata:
       name: my-app-service
     spec:
       selector:
         app: my-app
       ports:
       - protocol: TCP
         port: 80
         targetPort: 80
       type: LoadBalancer
     ```

2. **Apply the Service**:
   - Use `kubectl apply -f service.yaml` to create the service and expose the application.

### C. Monitoring and Scaling
- **Monitor**: Use AWS CloudWatch and Kubernetes metrics to monitor the health and performance of your applications.
- **Scale**: Use Kubernetes horizontal pod autoscaling or manual scaling to adjust the number of replicas based on load.

---

## 4. Integrating with AWS Services

### A. IAM Roles
- **Service Accounts**: Associate IAM roles with Kubernetes service accounts to provide permissions for accessing AWS services.

### B. ECR (Elastic Container Registry)
- **Push/Pull Images**: Use ECR to store and manage Docker container images used in your EKS cluster.

### C. CloudWatch Logs
- **Logging**: Configure EKS to send application logs to AWS CloudWatch Logs for centralized logging and monitoring.

---

## 5. Best Practices for EKS

### A. Security
- **IAM Policies**: Follow the principle of least privilege when assigning IAM policies.
- **Network Policies**: Use Kubernetes network policies to control traffic between pods.

### B. Cost Management
- **Resource Requests/Limits**: Define appropriate resource requests and limits for your containers.
- **Spot Instances**: Use EC2 Spot Instances to reduce costs for worker nodes.

### C. Cluster Maintenance
- **Update Regularly**: Keep your Kubernetes and EKS versions up to date to benefit from the latest features and security patches.
- **Backup and Restore**: Regularly back up your cluster configuration and application data.

---

## Summary
Today, we explored **Amazon EKS (Elastic Kubernetes Service)**, including how to set up a cluster, deploy applications, and integrate with AWS services. EKS simplifies Kubernetes management and provides powerful tools for running containerized applications at scale.

**Key Takeaways:**
- **EKS** provides a fully managed Kubernetes control plane.
- **Task Definitions** and **Services** help deploy and manage containerized applications.
- **Integration with AWS** services enhances EKS functionality and management.

---

### Next Session
In the next session, we will cover **Backup and Snapshot** to understand how to manage data protection and recovery in AWS.

---

**Thank you!**
