# Multi-Tier Banking Application

This repository contains a multi-tier banking application deployed on an AWS EC2 instance. The application is implemented using Java for the UI and MySQL for the database. This guide explains how to set up and deploy the project.

---

## Prerequisites
1. **AWS EC2 Instance**
   - Instance Type: `t2.micro` (or higher, based on requirements)
   - Operating System: Ubuntu 20.04 (or your preferred OS)

2. **Mobaxterm**
   - Used for SSH access to the EC2 instance.

3. **Java Development Kit (JDK)**
   - Ensure Java is installed on the instance.

4. **MySQL Server**
   - Installed for the database layer.

5. **Maven**
   - Used for building and packaging the Java application.

---

## Setup Instructions

### 1. Launch an EC2 Instance
- Create and start an EC2 instance with the necessary security group settings.
- Allow inbound traffic on ports `22`, `8080` (HTTP).

### 2. SSH into the EC2 Instance
Use Mobaxterm or your preferred SSH client to connect to the instance:
```bash
ssh -i your-key.pem ubuntu@<public-ip>
```

### 3. Install Java
Install Java to support the application:
```bash
sudo apt update
sudo apt install openjdk-11-jdk -y
```

### 4. Install MySQL Server
Set up the database server:
```bash
sudo apt install mysql-server -y
```
Log in to MySQL:
```bash
sudo mysql -u root
```
Change the root user password:
```sql
ALTER USER 'root'@'localhost' IDENTIFIED WITH mysql_native_password BY 'Test@123';
FLUSH PRIVILEGES;
```

### 5. Create the Database
Run the following commands to create and configure the database:
```sql
CREATE DATABASE bankappdb;
USE bankappdb;
-- Add necessary SQL queries to populate tables
SHOW DATABASES;
SHOW TABLES;
```

### 6. Build the Application
Clone the project and build it using Maven:
```bash
mvn compile
mvn test
mvn package
```
Navigate to the `target` folder to verify that the `.jar` file was created.

### 7. Run the Application
Start the application using the following command:
```bash
java -jar target/<filename>.jar
```
The application will start on the Tomcat server, accessible on port `8080`.

### 8. Access the Application
Access the application in a web browser using the EC2 Public IPv4 address and port `8080`:
```
http://<EC2-Public-IPv4>:8080
```

---

## Screenshots
### Dashboard View
![Dashboard Screenshot](https://github.com/user-attachments/assets/450c23f2-18ce-4099-bc22-d0e8272e3711)
![Screenshot (71)](https://github.com/user-attachments/assets/b026964e-c174-46a5-b596-be0ffd5e424c)


### EC2 Instance Details
![Screenshot (72)](https://github.com/user-attachments/assets/f692819b-db66-4460-8152-b4f4c30df96d)


### DB Details
![DB details (73)](https://github.com/user-attachments/assets/1e4d9d70-2b08-4524-9ce6-d442668ce620)

---

## Notes
- Ensure security groups allow traffic on port `8080`.
- Use strong passwords for MySQL and secure your EC2 instance.
- Always test your changes locally before deploying to EC2.

---

## License
[MIT License](LICENSE)
