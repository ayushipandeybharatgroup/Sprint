
#  SOP for Services

### This document provides a Standard Operating Procedure (SOP) for managing and monitoring Linux system services using `systemctl` commands.  
The example used here is the **Salary API** service from the OT-Microservices stack.

---

| **Author** | **Created on** | **Version** | **Last updated by** | **Last Edited On** | **Level** | **Reviewer** |
|-------------|----------------|--------------|---------------------|--------------------|------------|---------------|
| Ayushi | 2025-10-11 | 1.0 | Ayushi | 2025-10-11 | L0 | Komal Jaiswal |
| Ayushi | 2025-10-11 | 1.0 | Ayushi | 2025-10-11 | L1 | Imran |
| Ayushi | 2025-10-11 | 1.0 | Ayushi | 2025-10-11 | L2 | Shashi |

---

##  Table of Contents
- [Introduction](#introduction)
- [Purpose](#purpose)
- [Pre-requisites](#pre-requisites)
- [Service Management Steps](#service-management-steps)
  - [Check Service Status](#1-check-service-status)
  - [Stop Service](#2-stop-service)
  - [Start Service](#3-start-service)
  - [Enable Service](#4-enable-service)
  - [View Logs](#5-view-logs)
- [Screenshots](#screenshots)
- [Troubleshooting](#troubleshooting)
- [References](#references)
- [Author](#author)

---

##  Introduction
In the **OT-Microservices** architecture, backend components such as Salary API, Employee API, and Attendance API are deployed as Linux system services.  
Managing these services through `systemctl` ensures reliability, automatic startup on reboot, and easy monitoring.

---

##  Purpose
The purpose of this SOP is to:
- Define a standard procedure for service operations.
- Simplify management for microservices like `salary-api`.
- Help engineers troubleshoot service-level issues efficiently.

---

## Pre-requisites
Before managing any service:
1. You must have **sudo privileges**.
2. The service file should exist under `/etc/systemd/system/`.
3. Verify service name using:
   
   systemctl list-units --type=service | grep salary
   

---

##  Service Management Steps

### Check Service Status

sudo systemctl status salary-api


---

### Stop Service
sudo systemctl stop salary-api
sudo systemctl status salary-api



---

### Start Service

sudo systemctl start salary-api
sudo systemctl status salary-api


---

### Enable Service at Boot

sudo systemctl enable salary-api


---

### View Logs

sudo journalctl -u salary-api -f



> Press `Ctrl + C` to stop following logs and return to the terminal.

---

## Screenshots
Add all images under a `/assets` or `/images` folder in your repo, then link them like:

```
![Salary API Running](./assets/salary-status.png)
```


---

##  Troubleshooting

| **Issue** | **Cause** | **Solution** |
|------------|------------|---------------|
| Service not found | `.service` file missing | Check `/etc/systemd/system/` |
| Service failed to start | Port already in use | Check with `sudo lsof -i:8080` |
| Logs not showing | Wrong service name | Verify using `systemctl list-units` |
| Config changes not applied | Daemon not reloaded | Run `sudo systemctl daemon-reload` |

---

##  References

| **Topic** | **Link** | **Description** |
|------------|-----------|----------------|
| systemctl Docs | [https://www.freedesktop.org/software/systemd/man/systemctl.html](https://www.freedesktop.org/software/systemd/man/systemctl.html) | Official documentation |
| journalctl Guide | [https://man7.org/linux/man-pages/man1/journalctl.1.html](https://man7.org/linux/man-pages/man1/journalctl.1.html) | Log management guide |
| DigitalOcean Tutorial | [https://www.digitalocean.com/community/tutorials/how-to-use-systemctl](https://www.digitalocean.com/community/tutorials/how-to-use-systemctl) | Step-by-step example |

---

##💻 Author
| **Name** | **Email** |
|-----------|-----------|
| Ayushi | ayushi.snaatak@mygurukulam.co |

---

<p align="center">
  <em>End of Document</em>
</p>
