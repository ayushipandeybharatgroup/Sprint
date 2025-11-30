# Dependency Scanning POC

| Author      | Created on  | Version    | Last updated by | Last edited on | Internal reviewer |   L0     |    L1     |    L2   |
|-------------|-------------|------------|-----------------|----------------|-------------------|----------|-----------|-----------|
| Rajeev Ranjan    | 17-05-2025     | version 1  | N/A        |     N/A   |     Priyanshu         | Khushi Malhotra  | Mukul Joshi     | Piyush Upadhyay  |
| Rajeev Ranjan    | 17-05-2025     | version 1.1  | Khushi        |     03-06-2025   |     Priyanshu    | Khushi Malhotra  | Mukul Joshi     | Piyush Upadhyay  |

## Table of Contents
1. [Introduction](#1-introduction) 
2. [POC](#2-poc)
3. [Contact](#3-contact)
4. [References](#4-references)

## 1. Introduction
**What is Dependency Scanning in Golang CI?**

- In modern software development, dependency scanning is an essential practice to ensure the security, stability, and reliability of a project. In the context of Go (Golang) projects, this involves identifying vulnerabilities in both your codebase and the third-party libraries (dependencies) that your project uses.

## 2. POC 


### Step 1: Clone or Access the API Project

- If the API repository is hosted on a platform like GitHub, GitLab, or Bitbucket, you can clone it using the following command:

```bash
git clone https://github.com/OT-MICROSERVICES/employee-api.git
cd repository-name
```
![Screenshot 2025-05-17 204106](https://github.com/user-attachments/assets/79cb953b-2990-4c20-b728-557465731f0d)

---

### Step 2:   Install Go

- Install Go in you VM

```bash
wget https://go.dev/dl/go1.22.1.linux-amd64.tar.gz
sudo tar -C /usr/local -xzf go1.22.1.linux-amd64.tar.gz
export PATH=$PATH:/usr/local/go/bin
source ~/.bashrc
go version
```

![Screenshot 2025-05-17 204137](https://github.com/user-attachments/assets/ab534fa5-5c8d-4d8d-8b39-956c04b5d45d)


### Step 3:   Go Project Setup



**Dependencies**

- To get started, you need to install the following dependencies:

- [gorilla/mux](https://github.com/gorilla/mux) - A powerful URL router and dispatcher for Go. mux helps routes work (e.g., “when someone visits /employee, show data”).
- [logrus](https://github.com/sirupsen/logrus) - Structured logger for Go. logrus helps log things cleanly (e.g., “User tried to log in”).


**Installation**

- Run the following commands to install the necessary dependencies:

```bash
go get github.com/gorilla/mux
go get github.com/sirupsen/logrus

```

![Screenshot 2025-05-17 204154](https://github.com/user-attachments/assets/22cd854d-cdcc-4877-bb8e-8a18872e95e5)



- This will add the dependencies to the go.mod file, which tracks the Go dependencies for your project.

### Step 4: Inspect Dependencies Using go list
 
- To check all the dependencies your Go project is using, including transitive dependencies, you can run the `go list` command:

```bash
go list -m all
```

- This will display all the modules and dependencies for your project, helping you understand what is being used.

![Screenshot 2025-05-17 204210](https://github.com/user-attachments/assets/12dcc3ee-df29-42ab-9ebf-9dd442e9971b)


### Step 5. Clean Up Unused Dependencies with go mod tidy

- The `go mod tidy` command is useful for cleaning up any unused dependencies and ensuring that the `go.mod` and `go.sum` files are in sync. It also helps to find potentially outdated or unnecessary dependencies.

```bash
go mod tidy
```

- This command will remove any dependencies that are no longer needed and update your project’s dependency files.

![Screenshot 2025-05-17 204234](https://github.com/user-attachments/assets/8226a186-ccaa-4945-b2c1-24937832a109)


### Step 6:  Install GoSec

- To install GoSec, follow these steps:

1. **Run the following command** to install GoSec:

   ```bash
   sudo snap install gosec
   ```

 - This will install the latest version of GoSec

![Screenshot 2025-05-17 204302](https://github.com/user-attachments/assets/100b82fa-9d96-4946-91ec-9ba17b13d14e)


### Step 7: Verify GoSec Installation

- To ensure GoSec is installed correctly, run the following command:

```bash
gosec --version
```

- This should return the version of GoSec installed, confirming that the installation was successful.


### Step 8: Run GoSec to Scan the Employee API

- Now that GoSec is installed, you can use it to scan your Go code for security vulnerabilities.

#### Run GoSec on the Entire Project

- Navigate to your project root directory (where `main.go` and `go.mod` are located), and run the following command:

```bash
gosec ./...
```

- This will scan all Go files in the current directory and its subdirectories, including dependencies listed in your `go.mod` file.

 **GoSec Output**

![Screenshot 2025-05-17 204318](https://github.com/user-attachments/assets/0717f0ed-169d-4e43-a7ab-72458b2f0a33)

![Screenshot 2025-05-17 204341](https://github.com/user-attachments/assets/98433b8e-4d77-4408-aca2-ec19aecb561d)

![Screenshot 2025-05-17 204353](https://github.com/user-attachments/assets/2e647dd4-87a6-4ebc-a460-b119b7761886)

## 3. Contact 

| Name| Email Address      |
|-----|--------------------------|
| Rajeev Ranjan          |     rajeev.rajan.snaatak@mygurukulam.co |

## 4. References

1. [GoSec Documentation](https://github.com/securego/gosec)
2. [Snyk Official Site](https://snyk.io/)
3. [Dependabot Documentation](https://docs.github.com/en/github/administering-a-repository/keeping-your-dependencies-updated-automatically)
4. [GolangCI-Lint Documentation](https://golangci-lint.run/)
5. [Trivy GitHub Repository](https://github.com/aquasecurity/trivy)
