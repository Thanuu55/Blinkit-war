# Blinkit WebApp WAR Deployment on Apache Tomcat (AWS EC2)

This guide explains how to deploy a **Java Maven Web Application (WAR)** on an **Ubuntu AWS EC2 server using Apache Tomcat 9**.

---

# Server Details

* Public IP: **13.201.189.38**
* OS: **Ubuntu**
* Java Version: **OpenJDK 17**
* Web Server: **Apache Tomcat 9**
* Build Tool: **Maven**

---

# Step 1: Update Server

```bash
apt update
```

---

# Step 2: Install Java

Install Java 17 runtime required for Tomcat.

```bash
apt install openjdk-17-jre-headless -y
```

Verify installation:

```bash
java -version
```

---

# Step 3: Download Apache Tomcat

```bash
wget https://dlcdn.apache.org/tomcat/tomcat-9/v9.0.115/bin/apache-tomcat-9.0.115.tar.gz
```

Extract the archive:

```bash
tar -zxvf apache-tomcat-9.0.115.tar.gz
```

Remove the downloaded archive:

```bash
rm -rf apache-tomcat-9.0.115.tar.gz
```

---

# Step 4: Start Tomcat Server

Navigate to the Tomcat `bin` directory:

```bash
cd apache-tomcat-9.0.115/bin
```

Start the server:

```bash
sh startup.sh
```

---

# Step 5: Configure Tomcat Manager User

Edit the Tomcat users configuration file:

```bash
vi apache-tomcat-9.0.115/conf/tomcat-users.xml
```

Add the following inside the `<tomcat-users>` tag:

```xml
<role rolename="manager-gui"/>
<role rolename="manager-script"/>
<role rolename="manager-jmx"/>
<role rolename="manager-status"/>

<user username="admin" password="admin"
roles="manager-gui,manager-script,manager-jmx,manager-status"/>
```

---

# Step 6: Allow Remote Access to Manager App

Edit the manager context configuration:

```bash
vi apache-tomcat-9.0.115/webapps/manager/META-INF/context.xml
```

Remove or comment the following section to allow remote access:

```xml
<Valve className="org.apache.catalina.valves.RemoteAddrValve"
allow="127\.\d+\.\d+\.\d+|::1" />
```

---

# Step 7: Restart Tomcat

Stop Tomcat:

```bash
cd apache-tomcat-9.0.115/bin
sh shutdown.sh
```

Start Tomcat again:

```bash
sh startup.sh
```

---

# Step 8: Install Maven

Install Maven using script:

```bash
bash <(curl -sL https://tinyurl.com/52ykfnu5)
```

Reload bash configuration:

```bash
source ~/.bashrc
```

Verify Maven installation:

```bash
mvn --version
```

---

# Step 9: Clone the Project Repository

```bash
git clone https://github.com/dheer31/blinkit-webapp-war.git
```

Navigate to project directory:

```bash
cd blinkit-webapp-war
```

View project structure:

```bash
tree
```

---

# Step 10: Build the WAR File

Run Maven build:

```bash
mvn clean package
```

After build completes, the WAR file will be generated inside:

```
target/
```

---

# Step 11: Deploy WAR to Tomcat

Copy the WAR file to the Tomcat webapps directory:

```bash
cp ~/blinkit-webapp-war/target/*.war ~/apache-tomcat-9.0.115/webapps/
```

Tomcat will automatically deploy the application.

---

# Step 12: Access the Application

Open the application in browser:

```
http://13.201.189.38:8080
```

Tomcat Manager:

```
http://13.201.189.38:8080/manager
```

Login Credentials:

```
username: admin
password: admin
```

---

# Project Repository

GitHub Repository:

```
https://github.com/dheer31/blinkit-webapp-war
```

---

# Tech Stack

* Java 17
* Maven
* Apache Tomcat 9
* AWS EC2 (Ubuntu)

---

# Deployment Workflow

1. Launch EC2 instance
2. Install Java
3. Install Tomcat
4. Configure Tomcat Manager
5. Install Maven
6. Clone GitHub repository
7. Build WAR file
8. Deploy WAR into Tomcat
9. Access application via browser

---

# Author

Thanushri
Aspiring Java Full Stack Developer & DevOps Engineer



