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

| Layer | Technology |
|-------|------------|
| Frontend | React + Vite |
| Backend | Spring Boot + Maven |
| Database | MariaDB (RDS) |
| Cloud | AWS EC2, RDS |

## 🚀 Quick Deployment

### Backend
```bash
cd backend
mvn clean package
java -jar target/student-registration-backend-0.0.1-SNAPSHOT.jar
```

### Frontend
```bash
cd frontend
npm install
npm run build
sudo cp -r dist/* /var/www/html/
```

## Important Configs

**Backend `application.properties`**
See `backend/src/main/resources/application.properties`

**Frontend `.env`**
```env
VITE_API_URL=http://YOUR_BACKEND_IP:8080
```

⭐ Star if helpful!
