🚀 Full DevOps Stack with Kubeadm, Docker, Jenkins, Ansible, GitHub Webhooks & AWS
This project showcases a complete, end-to-end DevOps pipeline built with modern tools and best practices. It covers everything from infrastructure provisioning and configuration management to CI/CD automation, container orchestration, and cloud deployment — all powered by a self-managed Kubernetes cluster on AWS.

📌 Project Overview
What you’ll learn & implement:

✅ Provision AWS EC2 instances for infrastructure

✅ Install and configure Docker

✅ Set up a Kubernetes cluster using Kubeadm (Master & Worker nodes)

✅ Install and configure Jenkins for automated CI/CD

✅ Integrate GitHub Webhooks for automatic pipeline triggers

✅ Automate deployments with Ansible Playbooks

✅ Deploy applications continuously to Kubernetes

✅ Use GitHub as the source code and trigger mechanism

🛠 Tech Stack
Tool	Purpose
AWS EC2	Infrastructure hosting
Docker	Containerization
Kubeadm	Kubernetes cluster setup
Jenkins	Continuous Integration & Deployment
Ansible	Configuration management & automation
GitHub	Source code management
GitHub Webhooks	Automatic build & deployment triggers

📂 Project Structure
arduino
Copy code
├── ansible/
│   └── playbooks/
├── jenkins/
│   └── jobs/
├── k8s/
│   └── manifests/
├── scripts/
│   ├── install-docker.sh
│   └── setup-kubeadm.sh
├── Dockerfile
├── README.md
└── ...
⚙️ Setup Guide
1️⃣ Launch AWS EC2 Instances
Create at least 3 instances (1 master + 2 workers)

Open necessary ports: 22, 8080, 6443, etc.

2️⃣ Install Docker
bash
Copy code
sudo apt update
sudo apt install -y docker.io
sudo systemctl start docker
sudo systemctl enable docker
3️⃣ Set Up Kubernetes with Kubeadm
On Master Node:

bash
Copy code
sudo kubeadm init --pod-network-cidr=192.168.0.0/16
Configure a network plugin (Calico / Flannel)

Copy the kubeadm join command and run it on worker nodes

4️⃣ Install Jenkins
bash
Copy code
sudo apt update
sudo apt install -y openjdk-11-jdk
wget -q -O - https://pkg.jenkins.io/debian-stable/jenkins.io.key | sudo apt-key add -
sudo apt-add-repository "deb https://pkg.jenkins.io/debian-stable binary/"
sudo apt update
sudo apt install -y jenkins
Access Jenkins: http://<server-ip>:8080

Install recommended plugins

Create a Jenkins job and configure GitHub Webhook integration

5️⃣ Install Ansible
bash
Copy code
sudo apt update
sudo apt install -y ansible
Use an inventory file to define your target hosts

🔁 CI/CD Workflow
Developer pushes code to GitHub

GitHub Webhook triggers Jenkins

Jenkins:

Pulls the latest code

Builds a Docker image

Pushes the image to Docker Hub (optional)

Runs Ansible to deploy on Kubernetes

Application is updated in Kubernetes automatically

📚 Useful Commands
bash
Copy code
# Kubernetes nodes
kubectl get nodes

# Kubernetes pods
kubectl get pods

# Ansible ping test
ansible all -m ping -i inventory

# Jenkins logs
sudo journalctl -u jenkins
