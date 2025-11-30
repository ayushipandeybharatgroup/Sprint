#  Dependency Scanning – POC (OWASP Dependency Check)

This repository demonstrates a basic Proof of Concept (POC) of **Dependency Scanning** in a Maven-based Java application using the **OWASP Dependency-Check Maven Plugin**.  
The purpose of this POC is to detect security vulnerabilities in third-party libraries used in the project.

---

##  Table of Contents
1. [Objective](#-objective-of-the-poc)  
2. [Steps Performed](#-steps-performed)  
    <details>
      <summary>Steps</summary>
      
    - [Step 1 — Create Maven Project](#-step-1-—-create-maven-project)  
    - [Step 2 — Add OWASP Dependency-Check Plugin](#-step-2-—-add-owasp-dependency-check-plugin)  
    - [Step 3 — Install Dependencies & Build Tools](#-step-3-—-install-required-dependencies--build-tools)  
    - [Step 4 — Execute Dependency Scan](#-step-4-—-execute-dependency-scan)  
    - [Step 5 — Report Generation](#-step-5-—-report-generated) 
    </details>
3. [POC Output](#-output-of-the-poc)  
4. [Conclusion](#-conclusion)  
5. [References](#-references)  

---

##  Objective of the POC
✔ Enable security scanning inside a Maven project  
✔ Automatically identify vulnerable dependencies during build  
✔ Generate a detailed HTML security report  

---

##  Steps Performed

###  Step 1 — Create Maven Project
A simple Java application was created with standard Maven structure:

src/main/java
src/test/java
pom.xml



---

###  Step 2 — Add OWASP Dependency-Check Plugin
Add this plugin in `pom.xml` to enable dependency scanning:


    <build>
    <plugins>
        <plugin>
            <groupId>org.owasp</groupId>
            <artifactId>dependency-check-maven</artifactId>
            <version>9.2.0</version>
            <configuration>
                <nvdApiKey>YOUR_VALID_API_KEY</nvdApiKey>
                <autoUpdate>true</autoUpdate>
                <nvdApiDelay>10000</nvdApiDelay> <!-- 10 seconds delay -->
                <format>ALL</format>
                <dataDirectory>${project.build.directory}/dependency-check</dataDirectory>
                <failBuildOnAnyVulnerability>false</failBuildOnAnyVulnerability>
             </configuration>
             <executions>
                 <execution>
                     <goals>
                         <goal>check</goal>
                     </goals>
                 </execution>
             </executions>
         </plugin>
      </plugins>
    </build>
### Step 3 — Install Required Dependencies & Build Tools
   Ensure Maven 3.6+ and JDK 11+ are installed
   Add required dependencies like JUnit:


    <dependencies>
      <dependency>
        <groupId>junit</groupId>
        <artifactId>junit</artifactId>
        <version>4.13.2</version>
        <scope>test</scope>
      </dependency>
    </dependencies>
### Step 4 — Execute Dependency Scan
Run the following command:


mvn verify
During execution:

Project build starts

Dependency-Check analyzes all project dependencies

Checks CVE (Common Vulnerabilities & Exposures) database

### Step 5 — Report Generated
After scanning, an HTML report is created at:


    target/dependency-check-report.html
# Output of the POC
File / Folder	Description
pom.xml	Contains OWASP plugin and project configuration
target/dependency-check-report.html	Detailed vulnerability report



# Conclusion
This POC demonstrates that security scanning can be integrated directly into the development phase using the OWASP Dependency-Check plugin.
Every build now includes a vulnerability assessment, improving the security posture of the application.


# References
OWASP Dependency-Check Maven Plugin

NVD API Key Instructions

Maven Documentation

JUnit Official Documentation

pgsql
Copy code
