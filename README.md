# 🚀 React App with Docker and Ansible

## Overview
This project demonstrates how to **containerize a React.js application using Docker** and deploy it locally. Additionally, we use **Ansible** to automate the installation of **Node.js**.

## Features
✅ Automated **Node.js** installation with Ansible  
✅ **Multi-stage Docker build** for optimized image size  
✅ **Production-ready build** served via **Nginx**  
✅ **Dockerized environment** for easy deployment  
✅ **Port forwarding** to run the app on a specific port  

## Prerequisites
Before running this project, ensure the following dependencies are installed:  
- [Docker](https://docs.docker.com/get-docker/)  
- [Ansible](https://docs.ansible.com/ansible/latest/installation_guide/intro_installation.html)  

## 🛠 Technologies Used
- **React.js** – Frontend framework  
- **Docker** – Containerization  
- **Nginx** – Production server  
- **Ansible** – Automates Node.js installation  

## 📂 Project Structure
```
my-react-app/
│── src/                     # React source files
│── public/                  # Static files
│── Dockerfile               # Docker configuration
│── .dockerignore            # Ignore unnecessary files in Docker
│── package.json             # Project dependencies
│── README.md                # Documentation
```

## 🚀 Getting Started

### 1️⃣ Clone the Repository
```sh
git clone https://github.com/hasan914/my-react-app.git
cd my-react-app
```

## 1️⃣ Install Node.js Using Ansible  
Instead of manually installing Node.js, we use **Ansible**, a configuration management tool, to automate the installation process.

### Steps:
1. Create an **Ansible role** to install Node.js.  
2. Define an **Ansible playbook** to execute the role.  
3. Run the **playbook** to install Node.js on a Debian-based system.  

Run the following command to execute the **Ansible playbook**:  
```sh
ansible-playbook -i inventory nodejs-playbook.yml
```

## 2️⃣ Build and Run the React App with Docker

### 🔨 Build the Docker Image
To create a **Docker image** from the Dockerfile, run:
```sh
docker build -t hasanjaved667/react-app .
```

### 📤 Push the Image to Docker Hub
Once built, push the image to **Docker Hub**:
```sh
docker push hasanjaved667/react-app
```

### ▶️ Run the Container Locally
To start the **React app** inside a Docker container:
```sh
docker run -d -p 8080:80 --name react-app hasanjaved667/react-app
```
The app should now be accessible at [http://localhost:8080](http://localhost:8080) 🎉.

## 3️⃣ Why Use a Multi-Stage Dockerfile?  
A **multi-stage Dockerfile** helps **reduce image size** and **improve performance** by separating the build process from the runtime environment.

### Example Multi-Stage Dockerfile:
```dockerfile
# Stage 1: Build
FROM node:18 AS builder
WORKDIR /app
COPY package.json .
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Production
FROM nginx:latest
COPY --from=builder /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
```
### 🔥 Benefits:
- Reduces final **image size**
- Ensures a **clean runtime environment**
- Improves **security and performance**

## ✅ Conclusion
This project showcases how to:
1. **Automate Node.js installation** using **Ansible**  
2. **Containerize a React app** with **Docker**  
3. **Optimize the Docker image** using a **multi-stage build**  

## 📜 License
This project is licensed under the **MIT License**.

## 🙌 Contributing
Contributions are welcome!  
Feel free to **fork the repository** and submit a **pull request**.

### 🔗 Connect with Me  
📧 **LinkedIn:** [hasanjaved667](https://www.linkedin.com/in/hasanjaved667)  
🐙 **GitHub:** [hasan914](https://github.com/hasan914)  

---
Happy Coding! 🚀🔥

