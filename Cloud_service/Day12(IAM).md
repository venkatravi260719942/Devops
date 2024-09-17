# Day 12: AWS IAM (Identity and Access Management)

## 1. Introduction to IAM (Identity and Access Management)

### What is IAM?
**AWS IAM (Identity and Access Management)** is a service that enables you to securely manage access to AWS resources. It allows you to create and manage AWS users, groups, roles, and policies, controlling who can access specific resources and what actions they can perform.

### Key Concepts:
- **Users**: Individual identities that can access AWS services and resources.
- **Groups**: Collections of users with shared permissions.
- **Roles**: AWS identities with specific permissions that can be assumed by users, applications, or AWS services.
- **Policies**: JSON documents that define permissions for users, groups, and roles.

---

## 2. Managing IAM Users

### A. Creating a User
1. **Log in to the AWS Management Console**.
   - Navigate to the **IAM Dashboard**.

2. **Create a User**:
   - Click **Users** and then **Add user**.
   - Enter a **User name** and select **Access type** (e.g., programmatic access, AWS Management Console access).
   - Click **Next: Permissions**.

3. **Assign Permissions**:
   - Choose to attach existing policies directly, add the user to a group with policies, or copy permissions from an existing user.
   - Review and click **Create user**.

4. **Access Credentials**:
   - Save the access key ID and secret access key for programmatic access.
   - For console access, provide the user with the console login URL and temporary password.

### B. Managing User Permissions
- **Modify User Permissions**: Update permissions by adding or removing policies or changing group memberships.
- **View User Access**: Review the permissions and access history for individual users.

---

## 3. Managing IAM Groups

### A. Creating a Group
1. **Navigate to Groups**:
   - On the IAM Dashboard, click **Groups** and then **Create New Group**.

2. **Define Group Settings**:
   - Provide a **Group name** and select policies to attach.
   - Click **Create Group**.

3. **Add Users to Group**:
   - After creating the group, add users to it from the **Group details** page.

### B. Managing Group Permissions
- **Edit Group Permissions**: Update group policies to modify permissions for all group members.
- **Review Group Membership**: Check the users within each group and their associated permissions.

---

## 4. Managing IAM Roles

### A. Creating a Role
1. **Navigate to Roles**:
   - On the IAM Dashboard, click **Roles** and then **Create role**.

2. **Define Role Type**:
   - Choose the trusted entity type (e.g., AWS service, another AWS account).

3. **Attach Policies**:
   - Select policies to attach to the role.
   - Optionally, set up **role trust relationships** to specify who can assume the role.

4. **Create the Role**:
   - Review and click **Create role**.

### B. Using Roles
- **Assume Role**: Users or services assume the role to gain temporary access to the associated permissions.
- **Role for EC2**: Assign roles to EC2 instances to allow access to AWS resources from within the instance.

---

## 5. Managing IAM Policies

### A. Creating and Managing Policies
1. **Navigate to Policies**:
   - On the IAM Dashboard, click **Policies** and then **Create policy**.

2. **Define Policy Document**:
   - Use the JSON editor or policy generator to define permissions.
   - Example policy to allow S3 read access:
     ```json
     {
       "Version": "2012-10-17",
       "Statement": [
         {
           "Effect": "Allow",
           "Action": "s3:GetObject",
           "Resource": "arn:aws:s3:::your-bucket-name/*"
         }
       ]
     }
     ```

3. **Attach Policies**:
   - Attach policies to users, groups, or roles to enforce permissions.

### B. Policy Types
- **Managed Policies**: AWS provides predefined policies for common use cases.
- **Inline Policies**: Custom policies attached directly to users, groups, or roles.

---

## 6. Best Practices for IAM

### A. Security
- **Least Privilege**: Grant only the permissions necessary for users and services to perform their tasks.
- **Multi-Factor Authentication (MFA)**: Enable MFA for additional security, especially for privileged accounts.

### B. Monitoring and Auditing
- **IAM Access Advisor**: Review permissions used by IAM entities to identify and remove unused permissions.
- **CloudTrail**: Use AWS CloudTrail to monitor and log IAM activities for auditing purposes.

### C. Regular Reviews
- **Review Permissions**: Regularly review and adjust IAM policies and permissions to align with current requirements.
- **Rotate Credentials**: Regularly rotate IAM user access keys and passwords for improved security.

---

## Summary
Today, we covered **AWS IAM (Identity and Access Management)**, including how to manage users, groups, roles, and policies. IAM is essential for securely managing access to AWS resources and ensuring proper permissions.

**Key Takeaways:**
- **IAM Users**, **Groups**, and **Roles** help manage access and permissions.
- **Policies** define what actions are allowed for each entity.
- Implement **best practices** for security, monitoring, and regular reviews.

---

### Next Session
In the next session, we will cover **Git** to understand version control and collaboration in development.

---

**Thank you!**
