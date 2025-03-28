    TOOl-WISE QUESTION & ANSWERS
    ==============================
LINUX:::

IQ] what is the diff between bin and sbin?

--> /bin: Basic commands available to all users.

EX: ls, cat, cp, mv, rm, etc.

--> /sbin: System management commands, mostly for the root user.

EX: shutdown, reboot, ifconfig, mount, fsck, etc.

IQ] In which dir all the external software's?

Ans: /opt

IQ] what is command?

In Linux, a command is a specific instruction given to the operating system to perform a task.

IQ] what is a program?

It is a collection of instructions

IQ] we have 100 lines file, How to display 35 to 50 lines of data?

Ans:  head -50 file.txt | tail -15 

IQ] what is the diff between 400 and ugo+r
AN) Use numerical (400, 444, etc.) when scripting or setting precise permissions.
    Use symbolic (ugo+r, u-w, etc.) when adjusting permissions dynamically or for readability.




    MAVEN
========================================================

IQ] diff b/w install and deploy?

mvn install→ Builds and installs the artifact in the **local repository (`~/.m2/repository`)** for local use.  
mvn deploy → Uploads the artifact to a **remote repository (e.g., Nexus, Artifactory)** for team or production use.  

Use install -> when testing locally.  
Use deploy -> when sharing with others.

IQ] can we use more than one goal name along with mvn command?
ANS: Yes
EX:  mvn clean package [first it will execute clean and then package]

IQ] How to skip the unit test cases?

EX: mvn clean package -DskipTests
    mvn clean package -Dmaven.test.skip=true

IQ] where the maven default home dir?

  cd ~/.m2/repository/

  ls -lrth ---> you will see the dependecies.

IQ] How to change the maven default dir?
ANS:
   step 1: cd ~ ---> goto home dir
   step 2: create one custom dir --->   mkdir mavenlocalrepo
   step 3:  /root/customMavenRepo/  -----> copy this path
   step 4: <localRepository>/root/customMavenRepo</localRepository>  ---> add this into /conf/settings.xml  

   step 5: cd /opt/apache-maven-3.9.8/conf/
   step 6: open the settings.xml
   step 7: add this <localRepository>/root/mavenlocalrepo/</localRepository>
  
NOTE: Now you can run the mvn clean package : It will again downloading from centrol repo.

IQ] Then what is the use of mvn clean install?
ANS: It will store a package in maven local repo ---> /root/mavenlocalrepo/com/   Here it   will store.

  mvn clean install  ---> It will create package into maven local repo and target dir.



SONAR
======================================================

what is the diff between code review and code coverage?
=========================================================

code coverage:
--------------

Number of lines tested through unit test cases called as code coverage.

In any project 80% need to satisfy.

Benefits: Helps identify untested areas of code

Tools: Tools like JaCoCo (for Java)

code review:
------------

Code review is the process of manually reviewing code by team members to find bugs, ensure to following  coding standards, and improve overall code quality.

Benefits: It Leads to better software quality, fewer bugs, and promotes best practices within the development team.

Tools: Code review tools include GitHub Pull Requests.

Quality Profile
---------------
-> Collection of rules , those can be applied during the sonarqube generation.
-> For each language one quality profile will be there

quality gates
--------------
--> set of conditions

--> By default one quality gate is avaiable, i.e Sonar way



NEXUS
==========================

IQ] what is the difference between GitHub and nexus?

GitHub: used to manage the source code.
Nexus : used to manage the build artifacts.


IQ] why it is always uploading into snapshot repo, why not release repo?

ANS: In pom.xml <version> tag we defined "snapshot" , If you remove that tag then it will store in the release repo.

add  <version>1.0.0</version>

IQ] what is the difference between snapshot and release ?

SNAPSHOT: used in continuous deployment.
Release : Before deploy into production.

IQ] How to store artifacts into maven local repository?

   mvn clean install

IQ] How to store artifacts into maven remote repository?

  mvn clean deploy

  TOMCAT
  ==================================

IQ] Why Use Tomcat?

  Most projects now use Microservices Architecture.
  Java microservices are often developed using Spring Boot, which uses Tomcat as the default application server.

  
 IQ] Web Servers vs Application Servers
  
  Ans: Web Servers:  Handle static requests
                     Apache HTTPD, Nginx
                     Load balancing

  Application Servers:Business logic, dynamic content
  
                    :Tomcat, WildFly
                    :Business logic processing



 IQ} tomcat directory structure  


  Ans:# **Tomcat Directory Structur

   Main Directories & Their Purpose**

📂 bin/** *(Startup & Control Scripts)*
- Contains scripts to **start, stop, and manage** Tomcat.
- **Important Files:**
  - `startup.sh` → Starts Tomcat
  - `shutdown.sh` → Stops Tomcat
  - `catalina.sh` → Main Tomcat control script
  - `version.sh` → Displays Tomcat version

📂 conf/** *(Configuration Files)*
- Stores all **Tomcat configuration settings**.
- **Important Files:**
  - `server.xml` → Main configuration file (ports, connectors, etc.)
  - `web.xml` → Global web application settings
  - `tomcat-users.xml` → Defines users & roles
  - `context.xml` → Default application context settings

📂 lib/** *(Libraries & Dependencies)*
- Contains **Tomcat’s core Java libraries**.
- Additional JAR files (e.g., JDBC drivers) can be placed here.

📂 logs/** *(Log Files)*
- Stores **server activity, errors, and request logs**.
- **Important Logs:**
  - `catalina.out` → Main Tomcat log file
  - `localhost_access_log.*` → HTTP request logs

📂 temp/** *(Temporary Files)*
- Used by Tomcat for **storing temporary data**.
- Cleared automatically upon restart.

📂 webapps/** *(Deploy Applications)*
- This is where **web applications (WAR files)** are placed.
- Tomcat automatically extracts and runs applications from this folder.
- **Example Structure:**
  ```
  webapps/
  ├── myapp/
  │   ├── index.jsp
  │   ├── WEB-INF/
  │   ├── META-INF/
  ```

📂 work/** *(Compiled JSP Files)*
- Stores **compiled JSP files** to improve performance.
- Tomcat converts JSP files into servlets and caches them here.

---
## **3. Quick Reference Table**
| Directory  | Purpose  |
|------------|---------|
| `bin/`  | Scripts to start/stop Tomcat |
| `conf/`  | Configuration files |
| `lib/`  | Java libraries & dependencies |
| `logs/`  | Log files for monitoring |
| `temp/`  | Temporary files generated by Tomcat |
| `webapps/`  | Web application deployment folder |
| `work/`  | Compiled JSP files |

---
## **4. Summary**
✅ **Put your apps in** `webapps/`
✅ **Edit configuration settings in** `conf/`
✅ **Check logs in** `logs/`
✅ **Use `bin/` scripts to start/stop Tomcat**

💡 **Analogy:**
- 🏠 **`conf/`** = House blueprint (configuration)
- 📦 **`webapps/`** = Rooms (your applications)
- 🔧 **`bin/`** = Switchboard (start/stop server)
- 📜 **`logs/`** = CCTV footage (monitoring logs)

Apache HTTPD Server (Web Server)



             

