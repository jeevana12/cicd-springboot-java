# End to End CI/CD implementation for Java based application using maven,Sonarqube, Argocd,Helm,Kubernetes

![image](https://github.com/user-attachments/assets/d937dde7-c401-48a0-ac6b-a55da0b2094a)

A CI/CD pipeline automates the process of integrating code changes (Continuous Integration) and deploying them to production (Continuous Deployment/Delivery).

### Jenkins Integration for CI/CD:
CI (Continuous Integration): Jenkins automates code building and testing when changes are pushed to a repository.

CD (Continuous Deployment): Jenkins triggers deployment pipelines by integrating plugins like Kubernetes, Argocd,Argo image updater pushing changes to production environments.

#### Steps to seamlessly implement a pipeline for a Java application:

## CI PROCESS:

### 1. Set Up Source Control:
   Use GitHub, GitLab, or Bitbucket to host the Java application code.
### 2. ways of Configuring Trigger for Jenkins Pipeline:
-- Poll SCM: Enable Poll SCM and set a cron-like schedule to check for changes or go for

-- Git Webhook: Configure a webhook in your Git repository

-- Create jenkins file to define the pipeline and When setting up a build in Jenkins, directly supply the jenkins script path so that it triggers pipeline.
### 3. Build automation: 
 Since we're using Docker as the agent to run the entire pipeline process inside the container, Maven is already configured within the Docker image, eliminating the need for separate installation. Therefore, we can directly add the Maven build steps to compile and package the application (e.g.,` mvn clean package`).
### 4. Code Quality Checks:
Integrate tools such as SonarQube for static code analysis and detecting code vulnerabilities. Additionally, ensure Jenkins is authenticated with SonarQube by providing the necessary credentials.
### 5. Containerization:
Build Docker images using a Dockerfile and push the image to a Docker registry. Provide the necessary credentials to Jenkins for accessing the registry.

## CD PROCESS:
Here's how Jenkins invokes CD: 
### Updating deployment files:
 After a successful build, test, and artifact creation in Jenkins, deployment can be triggered using various tools like Shell Scripting, Image Updater, or Ansible. In this case, Shell Script is used, where once the image is pushed to the Docker registry, it continuously monitors the registry and updates the Git repository with the new version in the manifest files.
### Deploying it on k8 :
 So, next start the cluster and deploy argocd controller using operators or through helm charts. I have deployed the Argo CD controller using Helm charts. It ensures that the state between the manifests folder and the Kubernetes cluster is maintained. Whenever a change is committed to the manifest files, Argo CD automatically deploys the updated configuration to the Kubernetes cluster. 
  Finally, Argo CD deploys the application on to the kubernetes cluster and application will be running on 2 pods as specified in deployment.yml





A CI/CD pipeline automates the process of integrating code changes (Continuous Integration) and deploying them to production (Continuous Deployment/Delivery).

### Jenkins Integration for CI/CD:
CI (Continuous Integration): Jenkins automates code building and testing when changes are pushed to a repository.

CD (Continuous Deployment): Jenkins triggers deployment pipelines by integrating plugins like Kubernetes, Argocd,Argo image updater pushing changes to production environments.

#### Steps to seamlessly implement a pipeline for a Java application:

## CI PROCESS:

### 1. Set Up Source Control:
   Use GitHub, GitLab, or Bitbucket to host the Java application code.
### 2. ways of Configuring Trigger for Jenkins Pipeline:
-- Poll SCM: Enable Poll SCM and set a cron-like schedule to check for changes or go for

-- Git Webhook: Configure a webhook in your Git repository

-- Create jenkins file to define the pipeline and When setting up a build in Jenkins, directly supply the jenkins script path so that it triggers pipeline.
### 3. Build automation: 
 Since we're using Docker as the agent to run the entire pipeline process inside the container, Maven is already configured within the Docker image, eliminating the need for separate installation. Therefore, we can directly add the Maven build steps to compile and package the application (e.g.,` mvn clean package`).
### 4. Code Quality Checks:
Integrate tools such as SonarQube for static code analysis and detecting code vulnerabilities. Additionally, ensure Jenkins is authenticated with SonarQube by providing the necessary credentials.
### 5. Containerization:
Build Docker images using a Dockerfile and push the image to a Docker registry. Provide the necessary credentials to Jenkins for accessing the registry.

## CD PROCESS:
Here's how Jenkins invokes CD: 
### Updating deployment files:
 After a successful build, test, and artifact creation in Jenkins, deployment can be triggered using various tools like Shell Scripting, Image Updater, or Ansible. In this case, Shell Script is used, where once the image is pushed to the Docker registry, it continuously monitors the registry and updates the Git repository with the new version in the manifest files.
### Deploying it on k8 :
 So, next start the cluster and deploy argocd controller using operators or through helm charts. I have deployed the Argo CD controller using Helm charts. It ensures that the state between the manifests folder and the Kubernetes cluster is maintained. Whenever a change is committed to the manifest files, Argo CD automatically deploys the updated configuration to the Kubernetes cluster. 
  Finally, Argo CD deploys the application on to the kubernetes cluster and application will be running on 2 pods as specified in deployment.yml





   
