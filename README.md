# 📌 ToDo - Java Web Application  

## 🚀 Overview  
ToDo is a Java-based web application that allows users to register, log in, and manage their tasks efficiently. It utilizes JDBC, Servlets, JSP, and MySQL for backend operations and Apache Tomcat as the web server.

## ⚙️ Software Requirements  

### 1️⃣ Java Development Kit (JDK)  
- **Recommended:** JDK 17  
- [Download JDK 17](https://download.oracle.com/java/17/archive/jdk-17.0.12_windows-x64_bin.msi)  

### 2️⃣ Database  
- **MySQL 8** (or **Oracle 10g XE**)  
- [Download MySQL](https://dev.mysql.com/get/Downloads/Connector-J/mysql-connector-j-9.2.0.zip)  

### 3️⃣ IDE  
- Eclipse Enterprise Edition (or **NetBeans/IntelliJ**)  
- [Download Eclipse](https://www.eclipse.org/downloads/)  

### 4️⃣ Java Web Server  
- **Apache Tomcat 8.5+**  
- [Download Tomcat](https://apache.root.lu/tomcat/tomcat-8/v8.5.93/bin/apache-tomcat-8.5.93-windows-x64.zip)  
---

## 🛠️ Environment Setup  

### 1️⃣ Set Java Environment Variables  
- Add `C:\Program Files\Java\jdk-17\bin` to **System PATH**.  
- Set:  
  - **JAVA_HOME** → `C:\Program Files\Java\jdk-17`  
  - **CLASSPATH** → `.;`  

### 2️⃣ Setup MySQL Database  
- Open **MySQL Workbench** or **XAMPP Control Panel**  
- Create a new database:  
  ```sql
  CREATE DATABASE sbb3_todo;
    
    CREATE TABLE sbb3_todo.register (
        regid INT PRIMARY KEY,
        fname VARCHAR(20),
        lname VARCHAR(20),
        email VARCHAR(50),
        pass VARCHAR(20),
        mobile BIGINT,
        address VARCHAR(100)
    );

    CREATE TABLE sbb3_todo.tasks (
        taskid INT,
        taskname VARCHAR(50),
        taskdate VARCHAR(10),
        taskstatus INT CHECK (taskstatus IN (1,2,3)),
        regid INT,
        PRIMARY KEY (taskid, regid),
        FOREIGN KEY (regid) REFERENCES register(regid)
    );

    CREATE TABLE taskid_pks (
        regid INTEGER,
        taskid INTEGER,
        CONSTRAINT taskid_pks_regid_fk 
        FOREIGN KEY(regid) REFERENCES register(regid)
    );
    ```

    ---

## 🏗️ Project Structure  

```
sbb3_todo/
│── src/main/java
│   ├── beans
│   │   ├── Register.java
│   │   ├── Task.java
│   ├── factory
│   │   ├── DBConn.java
│   ├── dao
│   │   ├── ToDoDAO.java
│   │   ├── ToDoDAOImpl.java
│   ├── servlets
│   │   ├── RegisterServlet.java
│   │   ├── LoginServlet.java
│   │   ├── AddTaskServlet.java
│   │   ├── MarkTaskCompletedServlet.java
│   │   ├── LogoutServlet.java
│── src/main/webapp
│   ├── Register.html
│   ├── Login.jsp
│   ├── ViewTasks.jsp
│   ├── WEB-INF
│   │   ├── web.xml
│── lib/ (MySQL Connector JAR)
│── README.md
```


## 🔧 How to Run  

### 1️⃣ Clone the Repository  
```sh
git clone https://github.com/your-username/sbb3_todo.git
cd sbb3_todo
```

### 2️⃣ Import the Project into Eclipse
Open Eclipse
File → Import → Existing Projects into Workspace
Select sbb3_todo and click Finish

### 3️⃣ Add MySQL JDBC Connector
Right-click on the project
Go to Properties → Java Build Path → Libraries
Click on "Add External JARs"
Select mysql-connector-java-8.2.0.jar and click Apply & Close

### 4️⃣ Deploy the Application
Right-click the project
Run As → Run on Server
Select Apache Tomcat 8.5 and click Finish
