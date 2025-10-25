<p align="center">
  <img src="https://upload.wikimedia.org/wikipedia/commons/2/28/Gunicorn_logo_2010.svg" alt="Gunicorn Logo" width="250"/>
</p>

#  Gunicorn — Introduction & Key Features

### This document provides an overview of **Gunicorn (Green Unicorn)** — a Python WSGI HTTP Server used for deploying web applications such as Flask, Django, and FastAPI in production environments.

---

| **Author** | **Created on** | **Version** | **Last updated by** | **Last Edited On** | **Level** | **Reviewer** |
|-------------|----------------|--------------|---------------------|--------------------|------------|---------------|
| Ayushi | 2025-10-12 | 1.0 | Ayushi | 2025-10-12 | L0 | Komal Jaiswal |
| Ayushi | 2025-10-12 | 1.0 | Ayushi | 2025-10-12 | L1 | Imran |
| Ayushi | 2025-10-12 | 1.0 | Ayushi | 2025-10-12 | L2 | Shashi |

---

##  Table of Contents
- [Introduction](#introduction)
- [Purpose](#purpose)
- [What is Gunicorn](#what-is-gunicorn)
- [Why Use Gunicorn](#why-use-gunicorn)
- [Key Features](#key-features)
- [How Gunicorn Works](#how-gunicorn-works)
- [Basic Commands](#basic-commands)
- [Integration Example](#integration-example)
- [Troubleshooting](#troubleshooting)
- [References](#references)
- [Author](#author)

---

##  Introduction
In modern web architecture, **Gunicorn** acts as the **gateway between Python applications and web servers** like Nginx.  
It ensures smooth handling of multiple HTTP requests, high performance, and reliable scalability — making it a standard for production-grade Python deployments.

---

##  Purpose
The purpose of this document is to:
- Provide a standard introduction to **Gunicorn**.
- Explain **why** it’s used and **how** it fits in backend deployment.
- Highlight its **core features** and **usage examples** for developers managing production servers.

---

##  What is Gunicorn?
Gunicorn (**Green Unicorn**) is a **Python WSGI HTTP Server** that runs Python web applications efficiently in production environments.  
It’s a **pre-fork worker model** server — meaning it spawns multiple worker processes to handle concurrent requests.

**WSGI** stands for *Web Server Gateway Interface*, a standard interface between web servers and Python applications.

Command to use Gunicorn 
<img width="1186" height="410" alt="Screenshot 2025-10-24 194924" src="https://github.com/user-attachments/assets/d56ed3bb-33bf-4853-9b5c-def5f16113bc" />


Here is a sample site using Gunicorn for site broadcast
<img width="1365" height="669" alt="Screenshot 2025-10-24 194245" src="https://github.com/user-attachments/assets/d10e7b51-f893-49ec-964e-02ce6ac33e26" />

Running service in systemd so that it never faces downtime 
<img width="1364" height="670" alt="Screenshot 2025-10-24 201459" src="https://github.com/user-attachments/assets/b1779b51-38eb-4c9f-9207-821d7691317a" />



---

##  Why Use Gunicorn?
Built-in development servers like Flask’s `flask run` or Django’s `runserver` are not designed for production.  
Gunicorn provides:
- **Better concurrency** through worker processes  
- **Improved reliability** and uptime  
- **Automatic crash recovery**  
- **Easy scaling** and **load balancing** when paired with Nginx  

---

## ⚙️ Key Features

| **Feature** | **Description** |
|--------------|----------------|
|  **WSGI Compatible** | Works with any WSGI-compatible Python app (Flask, Django, FastAPI). |
|  **Pre-fork Worker Model** | Uses multiple worker processes for concurrent request handling. |
|  **Lightweight** | Simple, minimal, and fast with low memory usage. |
|  **Auto Worker Management** | Restarts failed or unresponsive workers automatically. |
|  **Easy Integration** | Works seamlessly with Nginx for load balancing and reverse proxying. |
|  **Highly Configurable** | Supports config files, CLI arguments, and environment variables. |
|  **Framework Agnostic** | Not tied to any specific Python web framework. |

---

##  How Gunicorn Works

**Process Flow:**


1️ Nginx receives HTTP requests from clients.  
2️ Requests are forwarded to Gunicorn.  
3️ Gunicorn translates them into WSGI calls for your Python app.  
4️ The app processes the request and sends the response back via Gunicorn and Nginx.  

---

##  Basic Commands

### Start Gunicorn
```bash
gunicorn app:app --bind 0.0.0.0:8000
