
## 🚀 Blinkit WebApp – Docker-Based CI/CD Deployment Flow

This project demonstrates an **end-to-end CI/CD pipeline** for deploying the **Blinkit Web Application** using **GitHub, Jenkins (Freestyle), Maven, Docker, and Tomcat**.

### 🔁 Deployment Flow

1. A developer pushes code changes to the **GitHub repository**.
2. A **GitHub Webhook** automatically triggers the Jenkins Freestyle job.
3. Jenkins pulls the latest source code and runs **Maven** to build the WAR file (`blinkit.war`).
4. Jenkins uses **Docker** to build an image that contains **Apache Tomcat** with the Blinkit WAR deployed.
5. The Docker container is started, exposing Tomcat on a configured port.
6. End users access the Blinkit web application through a web browser.

### 📊 CI/CD Architecture Flow

```
Developer → GitHub → Jenkins → Maven → Docker → Tomcat Container → Users
```

### 🛠 Tools & Technologies Used

* **Version Control:** GitHub
* **CI Tool:** Jenkins (Freestyle Project)
* **Build Tool:** Maven
* **Containerization:** Docker
* **Application Server:** Apache Tomcat
* **Deployment Environment:** Linux / Cloud VM

### ✅ Key Highlights

* Fully automated build and deployment pipeline
* No manual intervention after code push
* Containerized deployment ensures consistency across environments
* WAR-based enterprise web application deployment

---



