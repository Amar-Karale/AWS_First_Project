# 🎓 Student Registration App — AWS Full Stack Deployment

![AWS](https://img.shields.io/badge/AWS-EC2%20%7C%20RDS%20%7C%20VPC-FF9900?style=for-the-badge&logo=amazonaws&logoColor=white)
![Java](https://img.shields.io/badge/Java-Spring%20Boot-6DB33F?style=for-the-badge&logo=springboot&logoColor=white)
![React](https://img.shields.io/badge/React-Frontend-61DAFB?style=for-the-badge&logo=react&logoColor=black)
![MariaDB](https://img.shields.io/badge/MariaDB-RDS-003545?style=for-the-badge&logo=mariadb&logoColor=white)

A **production-grade full-stack web application** for student registration deployed on AWS.

## 🏗️ Architecture
- **Frontend**: React + Vite on EC2 with Apache2
- **Backend**: Spring Boot (Java 17) on EC2
- **Database**: MariaDB on Amazon RDS

## 🛠️ Tech Stack

| Layer      | Technology                  |
|------------|-----------------------------|
| Frontend   | React + Vite                |
| Backend    | Spring Boot + Maven         |
| Database   | MariaDB (RDS)               |
| Cloud      | AWS EC2, RDS                |

## 🚀 Full Deployment Guide on Ubuntu EC2

### 1. Backend Setup

```bash
# Update system
sudo apt update -y && sudo apt upgrade -y

# Clone repository
git clone https://github.com/Amar-Karale/AWS_First_Project.git
cd AWS_First_Project

# Go to backend
cd backend

# Install Java 17
sudo apt install openjdk-17-jdk -y
java -version

# Install Maven
sudo apt install maven -y
mvn -version

# Important: Edit database configuration
vim src/main/resources/application.properties
```

**Update in `application.properties`:**
- RDS Endpoint, Username, Password, Database name

```bash
# Build and run
mvn clean package

# Run in background (Recommended)
nohup java -jar target/student-registration-backend-0.0.1-SNAPSHOT.jar > backend.log 2>&1 &
```

### 2. Frontend Setup (Open new terminal)

```bash
# Go to frontend
cd ~/AWS_First_Project/frontend

# Install Node.js
sudo apt update -y
sudo apt install nodejs npm -y

# Edit .env file
vim .env
```

**Content for `.env`:**
```env
VITE_API_URL=http://YOUR_EC2_PUBLIC_IP:8080
```

```bash
npm install
npm run build

# Deploy with Apache
sudo apt install apache2 -y
sudo systemctl start apache2
sudo systemctl enable apache2

sudo rm -rf /var/www/html/*
sudo cp -rf dist/* /var/www/html/
sudo chown -R www-data:www-data /var/www/html/
```

## 🔧 Important Notes

- Allow ports **22**, **80**, and **8080** in EC2 Security Group
- Backend URL: `http://YOUR_IP:8080`
- Frontend URL: `http://YOUR_IP`

## 📋 Useful Commands

```bash
# Check services
ps aux | grep java
sudo systemctl status apache2

tail -f backend.log
sudo systemctl restart apache2
```

⭐ **Star this repo if it helped you!**

---
**Made by Amar Karale**
