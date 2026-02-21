# 🚀 Node.js CI/CD Pipeline using Jenkins & GitHub Webhook

This project demonstrates a fully automated **CI/CD pipeline** for a Node.js application. Whenever code is pushed to GitHub, Jenkins automatically builds and deploys the application to a remote target server.

---

## 📌 Project Overview

This pipeline automates the complete software delivery process:

- Local Node.js development  
- Code pushed to GitHub  
- GitHub webhook triggers Jenkins  
- Jenkins builds the application  
- Automatic deployment to target server  
- Application becomes live without manual steps  

---

## 🛠️ Tech Stack

- Node.js  
- Git & GitHub  
- Jenkins  
- GitHub Webhook  
- Linux (Ubuntu / EC2)  
- SSH  
- Nginx (optional)  
- PM2 (recommended)  

---

## 🏗️ CI/CD Architecture

```text
Developer → GitHub → Webhook → Jenkins → Build → Target Server → Live App
```

---

## 📂 Project Structure

```text
Node-App/
│
├── app.js
├── package.json
├── public/
├── views/
└── README.md
```

---

## ⚙️ Prerequisites

Before running this project, ensure:

- Jenkins server is running  
- Target server (EC2/VM) is ready  
- Node.js installed on target server  
- SSH access configured from Jenkins to target server  
- GitHub repository created  
- Webhook configured  

---

## 🔐 Jenkins Credentials Setup

In Jenkins:

**Manage Jenkins → Credentials → Global → Add Credentials**

Add the following:

- Kind: SSH Username with private key  
- Username: ubuntu (or your server user)  
- Private key: your server key  
- Credential ID: use a meaningful name  

This allows Jenkins to securely deploy to the target server.

---

## 🔧 GitHub Webhook Configuration

In your GitHub repository:

**Settings → Webhooks → Add webhook**

Configure:

Payload URL:

```
http://<jenkins-ip>:8080/github-webhook/
```

Content type: `application/json`  
Trigger: **Just the push event**

After saving, every push to GitHub will automatically trigger Jenkins.

---

## 🚀 Deployment Workflow

The automated pipeline performs the following actions:

1. Jenkins detects GitHub push via webhook  
2. Jenkins pulls latest source code  
3. Project dependencies are installed  
4. Build process executes  
5. Application files are copied to the target server  
6. Existing Node.js process is stopped  
7. Updated application is started on the server  
8. Application becomes live  

---

## 🌐 Access the Application

After successful deployment, access the app using:

```
http://<target-server-ip>:3000
```

Make sure the server security group allows the application port.

---

## 🧪 How to Test Automation

Make any change locally and push:

```bash
git add .
git commit -m "Test CI/CD"
git push
```

Jenkins pipeline should trigger automatically.

---

## 🛡️ Production Best Practices

For real-world deployments, consider:

- Use **PM2** for process management  
- Configure **Nginx reverse proxy**  
- Enable **HTTPS with SSL**  
- Add automated test stage  
- Add Docker containerization  
- Implement zero-downtime deployment  
- Add monitoring and logging  

---

## 👨‍💻 Author

**Sudarshan Mane**  
DevOps Enthusiast | Node.js Developer | CI/CD Practitioner

---

## ⭐ Support

If this project helped you, please give the repository a ⭐.
