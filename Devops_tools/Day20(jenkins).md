# Day 20: Jenkins (CI/CD)

## 1. Introduction to Jenkins

### What is Jenkins?
**Jenkins** is an open-source automation server used to automate the building, testing, and deploying of software. It is widely used for **Continuous Integration (CI)** and **Continuous Delivery (CD)** in software development pipelines.

### Key Concepts:
- **Continuous Integration (CI)**: The practice of merging code changes frequently into a shared repository, followed by automated testing and building.
- **Continuous Delivery (CD)**: The practice of automatically deploying code to production or staging environments after successful CI processes.
- **Pipeline**: A sequence of automated steps defined in code to handle building, testing, and deploying an application.
- **Plugins**: Jenkins has a rich ecosystem of plugins that extend its functionality, supporting a wide variety of tools, programming languages, and platforms.

---

## 2. Setting Up Jenkins

### A. Installing Jenkins
1. **Install Jenkins on Linux**:
   - Add the Jenkins repository and install Jenkins:
     ```bash
     sudo apt update
     sudo apt install openjdk-11-jdk
     wget -q -O - https://pkg.jenkins.io/debian/jenkins.io.key | sudo apt-key add -
     sudo sh -c 'echo deb http://pkg.jenkins.io/debian-stable binary/ > /etc/apt/sources.list.d/jenkins.list'
     sudo apt update
     sudo apt install jenkins
     ```

2. **Start Jenkins**:
   - Start Jenkins and enable it to run at boot:
     ```bash
     sudo systemctl start jenkins
     sudo systemctl enable jenkins
     ```

3. **Access Jenkins**:
   - Access Jenkins by opening `http://<your_server_ip>:8080` in a browser.

4. **Initial Setup**:
   - Unlock Jenkins by copying the administrator password from `/var/lib/jenkins/secrets/initialAdminPassword` and complete the setup wizard.

---

## 3. Jenkins Pipeline

### A. What is a Jenkins Pipeline?
A **Jenkins Pipeline** is a set of automated processes defined as code to build, test, and deploy software. Pipelines can be defined using either **Declarative** or **Scripted** syntax.

1. **Declarative Pipeline**: A more structured and simplified approach.
2. **Scripted Pipeline**: Provides more flexibility but is less readable.

### B. Writing a Declarative Pipeline
1. **Creating a Simple Pipeline**:
   - Navigate to Jenkins and create a new pipeline job. In the pipeline section, use the following example:
     ```groovy
     pipeline {
       agent any
       stages {
         stage('Build') {
           steps {
             echo 'Building...'
             // Add build commands here
           }
         }
         stage('Test') {
           steps {
             echo 'Testing...'
             // Add test commands here
           }
         }
         stage('Deploy') {
           steps {
             echo 'Deploying...'
             // Add deploy commands here
           }
         }
       }
     }
     ```

2. **Running the Pipeline**:
   - After saving the pipeline, click **Build Now** to run the pipeline. Jenkins will execute each stage (Build, Test, Deploy) in sequence.

### C. Scripted Pipeline Example
   - Here’s an example of a more flexible scripted pipeline:
     ```groovy
     node {
       stage('Build') {
         echo 'Building...'
         // Add build commands here
       }
       stage('Test') {
         echo 'Testing...'
         // Add test commands here
       }
       stage('Deploy') {
         echo 'Deploying...'
         // Add deploy commands here
       }
     }
     ```

---

## 4. Jenkins Plugins

### A. Popular Jenkins Plugins
1. **Git Plugin**: Integrates Git repositories with Jenkins for version control.
2. **Docker Plugin**: Allows Jenkins to interact with Docker containers and run builds inside them.
3. **Pipeline Plugin**: Provides support for Jenkins Pipelines as code.
4. **Email Extension Plugin**: Sends email notifications after a build completes or fails.
5. **SonarQube Plugin**: Integrates with SonarQube for code quality analysis.

### B. Installing Plugins
1. **Install via Jenkins Dashboard**:
   - Go to **Manage Jenkins** -> **Manage Plugins** -> **Available**, and search for the plugin you want to install.

2. **Restart Jenkins**:
   - Some plugins may require a restart to take effect.

---

## 5. Continuous Integration with Jenkins

### A. CI Workflow with Jenkins
1. **Code Check-in**: Developers push code changes to a version control system (e.g., Git).
2. **Automated Build**: Jenkins automatically pulls the latest changes and runs the build process.
3. **Automated Testing**: Jenkins runs unit tests or integration tests.
4. **Feedback**: Jenkins provides feedback to developers via build results or email notifications.

### B. Automating Builds with Git
1. **Integrating Jenkins with Git**:
   - Set up a pipeline that automatically triggers a build when changes are pushed to a Git repository.

2. **Example Jenkinsfile** for a Git-based CI pipeline:
   ```groovy
   pipeline {
     agent any
     stages {
       stage('Checkout') {
         steps {
           git 'https://github.com/example/my-repo.git'
         }
       }
       stage('Build') {
         steps {
           sh './build.sh'
         }
       }
       stage('Test') {
         steps {
           sh './test.sh'
         }
       }
     }
   }

3. **Continuous Delivery with Jenkins**
### A. CD Workflow with Jenkins
- **Automated Deployment**: After successful CI, Jenkins can automatically deploy the application to staging or production environments.
- **Rollbacks**: Jenkins can help automate rollbacks in case of a failed deployment.

### B. Setting up CD Pipelines
- **Using Jenkins with Docker for CD**:
Use the Docker Plugin to deploy applications in containers as part of the CD pipeline.
- **Example Jenkinsfile for CD**:
```groovy
pipeline {
  agent any
  stages {
    stage('Build') {
      steps {
        sh './build.sh'
      }
    }
    stage('Test') {
      steps {
        sh './test.sh'
      }
    }
    stage('Deploy') {
      steps {
        sh 'docker-compose up -d'
      }
    }
  }
}
```
## 7. Best Practices for Jenkins Pipelines
### A. Pipeline as Code
***Always define pipelines as code using Jenkinsfile. This allows version control and better collaboration.***

### B. Use Blue Ocean
***Install the Blue Ocean plugin for a modern Jenkins UI, simplifying pipeline creation and monitoring.***

### C. Secure Jenkins
***Implement role-based access control (RBAC) to limit access to sensitive operations.Secure Jenkins with HTTPS and use credentials management to handle secrets safely.***

### D. Backup Jenkins Configuration
***Regularly back up your Jenkins home directory, which contains job configurations, plugins, and system settings.***

---
# Summary
Today, we learned about Jenkins as a powerful tool for automating Continuous Integration (CI) and Continuous Delivery (CD). We explored how to set up Jenkins, define pipelines, install plugins, and automate the entire software development lifecycle.

## Key Takeaways:

Jenkins pipelines can automate build, test, and deploy processes.
Plugins expand Jenkins’ functionality for version control, Docker, notifications, and more.
Jenkins is an essential tool in CI/CD workflows for efficient and reliable software delivery.

### Next Session
In the next session, we will dive into Git to understand version control and collaboration in software development.

---
#### Thank you!