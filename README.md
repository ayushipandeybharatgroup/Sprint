Introduction

In any microservice-based architecture (like OT-Microservices), each backend or frontend application runs as a service on the Linux server.
Managing these services effectively is crucial for ensuring uptime, health, and availability of the entire application stack.

This SOP provides detailed steps and best practices to start, stop, enable, disable, and monitor services using systemctl.

Purpose

The purpose of this SOP is to:

Define a standard procedure for managing system services.

Ensure consistent operations across all environments (Dev, QA, Production).

Help engineers troubleshoot and recover services quickly.

Maintain system stability by properly enabling/disabling services during deployment.

Pre-requisites

Before performing service operations, ensure:

You have sudo/root privileges.

The service file exists in /etc/systemd/system/ (e.g., frontend.service, employee.service).

The service is correctly configured with the right path to the executable or script.

You understand the service’s dependencies (e.g., database, API).

Service Management Commands
🔹 Start a Service

Use this command to start a service manually.

sudo systemctl start <service-name>


Example:

sudo systemctl start frontend

🔹 Stop a Service

Stops the running service.

sudo systemctl stop <service-name>


Example:

sudo systemctl stop employee

🔹 Restart a Service

Use this after updating configuration or code changes.

sudo systemctl restart <service-name>


Example:

sudo systemctl restart salary

🔹 Enable a Service

Enable the service to auto-start at boot time.

sudo systemctl enable <service-name>


Example:

sudo systemctl enable notification

🔹 Disable a Service

Disable auto-start on boot.

sudo systemctl disable <service-name>


Example:

sudo systemctl disable frontend

🔹 Check Service Status

Displays whether the service is active, inactive, or failed.

sudo systemctl status <service-name>


Example:

sudo systemctl status attendance


You’ll see output like:

● attendance.service - Attendance API Service
   Loaded: loaded (/etc/systemd/system/attendance.service; enabled)
   Active: active (running) since Fri 2025-10-10 10:45:11 UTC; 2h 5min ago
   Main PID: 3125 (node)

🔹 View Service Logs

Use journalctl to check logs and debug issues.

sudo journalctl -u <service-name> -f


Example:

sudo journalctl -u frontend -f


(The -f flag follows the log in real-time.)

Common Examples
Operation	Command Example	Description
Start service	sudo systemctl start employee	Starts employee service
Stop service	sudo systemctl stop salary	Stops salary service
Restart service	sudo systemctl restart notification	Restarts notification service
Enable service at boot	sudo systemctl enable frontend	Auto-start frontend on system boot
Disable auto-start	sudo systemctl disable frontend	Prevents service from starting at boot
Check current status	sudo systemctl status frontend	Checks running status and uptime info
View logs	sudo journalctl -u frontend -f	Monitors real-time logs of the service
Troubleshooting
Issue	Possible Cause	Solution
Service not starting	Incorrect service file path or permissions	Check /etc/systemd/system/<service>.service and verify ExecStart path
Service fails immediately	Port already in use	Check with sudo lsof -i:<port> and free the port
Logs not showing	Wrong service name	Verify service name using systemctl list-units --type=service
Changes not taking effect	Daemon not reloaded	Run sudo systemctl daemon-reload after editing the service file
Contact Information
Name	Email Address
Ayushi	ayushi.snaatak@mygurukulam.co
References
Topic	Link	Description
systemctl documentation	https://www.freedesktop.org/software/systemd/man/systemctl.html
	Official systemctl command reference
journalctl usage	https://man7.org/linux/man-pages/man1/journalctl.1.html
	Log viewing and debugging
Linux Services Guide	https://www.digitalocean.com/community/tutorials/how-to-use-systemctl
	Tutorial for beginners
