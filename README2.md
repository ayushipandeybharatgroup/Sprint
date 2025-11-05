<p align="center">
  <img width="300" height="168" alt="image" src="https://github.com/user-attachments/assets/8e05e295-9250-4271-b906-51faad78ba61" />
</p>

# Golang Installation via Bash Script

---

| **Author** | **Created on** | **Version** | **Last Edited On** | **Level** | **Reviewer** |
|-------------|----------------|--------------|--------------------|------------|---------------|
| Ayushi | 2025-10-30 | 1.0 | 2025-11-4  | Internal Review | Aman |



---

This repository provides an automated Bash script to install or upgrade **Golang (Go programming language)** on any Linux system.  
The script supports multiple versions, upgrade/downgrade, and environment setup for all users or the current user.


## Table of Contents

- [Features](#features)  
- [Prerequisites](#prerequisites)  
- [Installation Script](#installation-script)  
- [Usage](#usage)  
- [Directory Structure](#directory-structure)  
- [Upgrade or Downgrade Go](#upgrade-or-downgrade-go)  
- [Uninstallation](#uninstallation)  
- [Test Installation](#test-installation)  
- [Troubleshooting](#troubleshooting)  
- [References](#references)  
- [Contact](#contact)

---

## Features

- Install or upgrade specific Go versions  
- Sets up environment variables (`GOROOT`, `GOPATH`, `PATH`)  
- Works on most Linux distributions (Ubuntu, Debian, CentOS, etc.)  
- Safe to re-run anytime  
- Verifies installation automatically  

---

## Prerequisites

Before running the script:

- Make sure you have **sudo privileges**  

Internet connection is required to download Go binaries

Installation Script
Save the script as install_golang.sh:

     #!/bin/bash

     # Simple Go installation script

     # Step 1: Update system
     sudo apt update -y

     # Step 2: Install Go (from Ubuntu repo)
     sudo apt install -y golang-go

     # Step 3: Verify installation
     go version

    # Step 4: Show Go environment path
    go env

    # Verify
     if go version >/dev/null 2>&1; then
     echo "✅ Golang installed successfully!"
     else
     echo "⚠️ Please run 'source ~/.bashrc' and try 'go version'"
     fi

After Installation via Bash Script
<img width="1081" height="405" alt="image" src="https://github.com/user-attachments/assets/727ad3ff-9c87-43ad-bf48-71fc2329b641" />

<img width="733" height="93" alt="image" src="https://github.com/user-attachments/assets/4f81258e-7246-498c-bb6c-b254863dd205" />


Usage:-
# Make the script executable
         chmod +x install_golang.sh

# Install default version
       ./install_golang.sh



# Verify installation
       go version

# Example Output:
    go version go1.23.2 linux/amd64

###  Go Directory Structure
After installation:

| Path | Description |
|------|--------------|
| `/usr/local/go` | Go installation directory |
| `~/go/bin` | Go binaries (executables) |
| `~/go/src` | Source code (your Go projects) |
| `~/go/pkg` | Compiled packages |

Upgrade or Downgrade Go
# To switch Go versions, simply run:
        ./install_golang.sh <version>
# Example:
      ./install_golang.sh 1.21.0
The script automatically removes the old version and installs the new one.

# Uninstallation
    #To completely remove Go:
    sudo rm -rf /usr/local/go
    rm -rf ~/go
    sed -i '/# Go environment setup/,+3d' ~/.bashrc
# Test Installation

    mkdir -p ~/go/src/hello
    cd ~/go/src/hello
    cat <<EOF > hello.go
     package main
    import "fmt"

     func main() {
    fmt.Println("Hello, Go is installed successfully!")
    }
    EOF

    go run hello.go

## Expected Output:
Hello, Go is installed successfully!

## Troubleshooting
Issue	Cause	Solution
command not found: go	Environment not loaded	Run source ~/.bashrc
Permission denied	Missing sudo rights	Run with sudo ./install_golang.sh
tar: Cannot open	Corrupt download	Delete file and retry



## Contact
| **Name** | **Email** |
|-----------|-----------|
| Ayushi | ayushi.snaatak@mygurukulam.co |

## References

| Reference | Description / Link |
|------------|--------------------|
| Official Go Downloads | [https://www.geeksforgeeks.org/installation-guide/how-to-install-go-programming-language-in-linux/) |


---

