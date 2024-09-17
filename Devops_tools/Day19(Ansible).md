# Day 19: Ansible

## 1. Introduction to Ansible

### What is Ansible?
**Ansible** is an open-source automation tool used for configuration management, application deployment, and task automation. It uses a simple, human-readable language called **YAML** (Yet Another Markup Language) to describe automation tasks.

### Key Concepts:
- **Playbooks**: YAML files that define tasks and how they should be executed on managed hosts.
- **Inventory**: A list of machines (hosts) Ansible will manage.
- **Modules**: Reusable scripts provided by Ansible to perform tasks such as installing software, copying files, and restarting services.
- **Roles**: A way to group related tasks, variables, and handlers for better organization.
- **Idempotency**: Ansible ensures tasks are repeatable, meaning no matter how many times you run a playbook, the result will always be the same.

---

## 2. Setting Up Ansible

### A. Installing Ansible
1. **Install Ansible on Linux/MacOS**:
   - Install Ansible using a package manager:
     ```bash
     sudo apt update && sudo apt install ansible -y  # Ubuntu/Debian
     sudo yum install ansible -y                     # CentOS/RHEL
     brew install ansible                            # macOS
     ```

2. **Install Ansible on Windows**:
   - Use the **Windows Subsystem for Linux (WSL)** or run Ansible in a Linux VM.

3. **Verify Installation**:
   - Check the Ansible version to confirm the installation:
     ```bash
     ansible --version
     ```

---

## 3. Working with Ansible

### A. Ansible Inventory
1. **Create an Inventory File**:
   - Create a file called `hosts` to define the machines Ansible will manage:
     ```ini
     [webservers]
     server1.example.com
     server2.example.com

     [dbservers]
     db1.example.com
     ```

2. **Use Dynamic Inventory**:
   - You can also use dynamic inventory from cloud providers like AWS, Azure, or GCP.

### B. Ansible Ad-Hoc Commands
1. **Run an Ad-Hoc Command**:
   - Use Ansible ad-hoc commands to perform tasks on hosts directly:
     ```bash
     ansible all -i hosts -m ping
     ```

2. **Install Software**:
   - Install software on remote hosts using the `apt` module:
     ```bash
     ansible webservers -i hosts -m apt -a "name=nginx state=present"
     ```

### C. Ansible Playbooks
1. **Create a Playbook**:
   - Write a simple playbook in YAML format (`site.yml`):
     ```yaml
     ---
     - name: Install and configure web server
       hosts: webservers
       become: true
       tasks:
         - name: Install NGINX
           apt:
             name: nginx
             state: present

         - name: Start NGINX service
           service:
             name: nginx
             state: started
     ```

2. **Run a Playbook**:
   - Execute the playbook using the `ansible-playbook` command:
     ```bash
     ansible-playbook -i hosts site.yml
     ```

### D. Ansible Modules
1. **Using Ansible Modules**:
   - Ansible comes with various modules for managing systems, cloud resources, and applications. For example, the `apt` module is used to manage packages in Debian-based systems, and the `yum` module is used in RedHat-based systems.
   - Example of using the `copy` module to copy files to remote hosts:
     ```yaml
     - name: Copy index.html to web server
       copy:
         src: /local/path/to/index.html
         dest: /var/www/html/index.html
     ```

2. **Finding Modules**:
   - To find available modules and usage details, run:
     ```bash
     ansible-doc -l
     ```

### E. Ansible Roles
1. **Create and Use Roles**:
   - Roles help organize playbooks into reusable components. Create a directory structure for a role:
     ```
     roles/
       webserver/
         tasks/
           main.yml
         handlers/
           main.yml
         files/
         templates/
         vars/
           main.yml
     ```

2. **Use a Role in a Playbook**:
   - Call the role in your main playbook:
     ```yaml
     ---
     - name: Configure web servers
       hosts: webservers
       roles:
         - webserver
     ```

### F. Ansible Galaxy
1. **Installing Roles from Ansible Galaxy**:
   - Ansible Galaxy is a repository of pre-built Ansible roles. Install a role directly from Galaxy:
     ```bash
     ansible-galaxy install geerlingguy.nginx
     ```

2. **Using Installed Roles**:
   - Include the downloaded role in your playbook like any other role.

---

## 4. Best Practices for Ansible

### A. Playbook Structure
- **Use Variables**: Define variables in separate files to keep playbooks clean.
- **Use Handlers**: Use handlers for tasks that should only run when notified, such as restarting a service.

### B. Idempotency
- Ensure your tasks are idempotent. Ansible should only make changes when necessary, not every time it runs.

### C. Role Reusability
- **Create Modular Roles**: Break down complex playbooks into reusable roles to maintain clean and efficient configurations.

### D. Security
- **Encrypt Sensitive Data**: Use `ansible-vault` to encrypt sensitive information such as passwords and API keys:
  ```bash
  ansible-vault encrypt vars/secret.yml

### E. Testing
- **Test Playbooks**: Use tools like Molecule to test your playbooks locally or in CI/CD pipelines.

---
# Summary
Today, we explored Ansible, covering the basics of playbooks, inventory, modules, and roles. Ansible is an essential tool for automating configuration management, allowing you to automate repetitive tasks and ensure consistency across environments.

## Key Takeaways:

Playbooks are YAML-based configurations for managing tasks.
Inventory defines the hosts to manage, and modules are the building blocks of tasks.
Use roles to organize and reuse automation tasks efficiently.

### Next Session

In the next session, we will dive into Jenkins (CI/CD) to understand continuous integration and delivery pipelines.

---
### Thank you!