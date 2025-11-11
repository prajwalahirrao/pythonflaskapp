# pythonflaskapp



# 🐳 Python Flask App - Dockerized on AWS EC2

## 📘 Overview

This project demonstrates how to **containerize and deploy a Python Flask web application** using **Docker** on an **AWS EC2 instance**.
It showcases basic DevOps skills such as image building, container management, and deployment on the cloud.

---

## 🧩 Tech Stack

| Component            | Technology               |
| -------------------- | ------------------------ |
| Programming Language | Python 3                 |
| Framework            | Flask                    |
| Containerization     | Docker, Docker Compose   |
| Cloud Platform       | AWS EC2 (Amazon Linux 2) |
| Version Control      | Git & GitHub             |

---

## ⚙️ Project Structure

```
pythonflaskapp/
├── app.py
├── requirements.txt
├── Dockerfile
└── README.md
```

---

## 🚀 Features

* Lightweight Python Flask web app
* Dockerized for consistent deployment
* Runs on AWS EC2 Linux instance
* Exposes port `5000` for web access
* Optional Docker Compose setup

---

## 🛠️ Setup and Deployment

### 1️⃣ Launch EC2 Instance

* Launch an **Amazon Linux 2** instance on AWS.
* Connect via **SSH** or **PuTTY**.

### 2️⃣ Install Required Packages

```bash
sudo yum update -y
sudo yum install git -y
sudo yum install docker -y
sudo systemctl start docker
sudo systemctl enable docker
```

### 3️⃣ Clone Repository

```bash
git clone https://github.com/prajwalahirrao/pythonflaskapp.git
cd pythonflaskapp/
```

### 4️⃣ Install Python & Flask (for testing)

```bash
sudo yum install python -y
sudo yum install pip -y
pip install flask
python app.py
```

### 5️⃣ Build Docker Image

```bash
sudo docker build -t prajwalahirrao/pythonflaskapp .
```

### 6️⃣ Run Container

```bash
sudo docker run -d -p 5000:5000 prajwalahirrao/pythonflaskapp
```

Check running container:

```bash
sudo docker ps
```

### 7️⃣ (Optional) Enable Docker Compose

```bash
sudo mkdir -p /usr/local/lib/docker/cli-plugins
sudo curl -SL https://github.com/docker/compose/releases/download/v2.27.0/docker-compose-linux-x86_64 \
  -o /usr/local/lib/docker/cli-plugins/docker-compose
sudo chmod +x /usr/local/lib/docker/cli-plugins/docker-compose
docker compose version
sudo docker compose up -d
```

---

## 🌐 Access the Application

In your browser, visit:
👉 **http://<your-ec2-public-ip>:5000**

---

## 🧰 Useful Docker Commands

| Action           | Command                           |
| ---------------- | --------------------------------- |
| List images      | `sudo docker images`              |
| List containers  | `sudo docker ps -a`               |
| Remove image     | `sudo docker rmi <image_id>`      |
| Stop container   | `sudo docker stop <container_id>` |
| Remove container | `sudo docker rm <container_id>`   |

---

## 📦 Dockerfile

```dockerfile
FROM python:3.9-slim
WORKDIR /app
COPY . .
RUN pip install -r requirements.txt
EXPOSE 5000
CMD ["python", "app.py"]
```
