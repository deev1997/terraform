# Terraform and Kubernetes Integration with Minikube

## Project Overview

This project demonstrates the integration of Terraform with a Kubernetes cluster powered by **Minikube**. The goal is to automate the provisioning, deployment, and management of infrastructure using **Terraform**, **Kubernetes**, and **GitHub Actions**.

### Key Technologies:
- **Minikube**: A local Kubernetes cluster used to simulate cloud Kubernetes environments like AWS EKS or Google GKE.
- **Terraform**: Infrastructure as Code (IaC) tool used to provision and manage Kubernetes resources.
- **GitHub Actions**: CI/CD pipeline tool that automates workflows like provisioning and deployment.

---

## Links and References

This project utilizes the following resources to achieve its goal:

1. **Minikube Start Guide**:
   - [Minikube Setup Guide](https://minikube.sigs.k8s.io/docs/start/?arch=%2Fmacos%2Fx86-64%2Fstable%2Fbinary+download)
     - Detailed documentation on how to install and configure Minikube for local Kubernetes clusters.

2. **Terraform and Kubernetes Integration with Minikube**:
   - [Medium Blog Post](https://medium.com/rahasak/terraform-kubernetes-integration-with-minikube-334c43151931)
     - Step-by-step tutorial on how Terraform interacts with Kubernetes clusters (Minikube in this case) to manage resources.

3. **Terraform GitHub Actions Automation**:
   - [HashiCorp Tutorial](https://developer.hashicorp.com/terraform/tutorials/automation/github-actions#verify-ec2-instance-provisioned)
     - Guide for automating Terraform with GitHub Actions. The integration will enable automatic infrastructure provisioning and deployment to Minikube via CI/CD pipelines.

---

## Project Workflow

### 1. **Minikube Setup in GitHub Actions**:
- Minikube is set up dynamically within a GitHub Actions pipeline. This eliminates the need for manual intervention on your local machine, making the process fully automated and cloud-ready.
- The `minikube` command starts the local Kubernetes cluster on GitHub’s hosted runners.

### 2. **Terraform Setup and Kubernetes Provider Configuration**:
- Terraform initializes and configures the Kubernetes provider, which is used to manage the resources on the Minikube cluster. Kubernetes authentication credentials (such as certificates) are securely handled by GitHub Actions.
  
### 3. **CI/CD Pipeline with GitHub Actions**:
- The GitHub Actions workflow is set up to:
  - **Checkout** the latest code.
  - **Install Terraform** and **kubectl**.
  - **Start Minikube** inside the pipeline.
  - **Generate a kubeconfig file** dynamically using the credentials stored in GitHub secrets.
  - **Run Terraform commands** (`terraform init`, `terraform plan`, `terraform apply`) to manage the Kubernetes resources.
  
### 4. **Deployment and Configuration**:
- Once the pipeline runs successfully, the Kubernetes resources (like Pods, Deployments, etc.) are provisioned on the Minikube cluster, providing a live environment for further testing and development.

---

## Prerequisites

To run this project, you will need:
- **Terraform**: Install Terraform to manage your infrastructure.
- **Minikube**: Setup Minikube on your local machine to simulate a cloud Kubernetes environment (though this project uses GitHub Actions to spin it up dynamically).
- **GitHub Account**: To run the pipeline and manage your project’s repository.

You can follow the setup guides here:
- [Minikube Installation](https://minikube.sigs.k8s.io/docs/start/)
- [Terraform Installation](https://www.terraform.io/downloads.html)

---

## How to Run the Project Locally

While this project is automated via GitHub Actions, you can test it locally with these steps:

### 1. Install Minikube and Terraform

Make sure that Minikube and Terraform are installed on your local machine. Follow the installation instructions provided in the documentation.

### 2. Initialize the Kubernetes Cluster

Run Minikube locally:
```bash
minikube start
