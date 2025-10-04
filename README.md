Born2beroot - Secure Virtual Machine Configuration 🛡️


A project to master Linux system setup and security hardening

Overview

Born2beroot is a system administration project from the 1337 School curriculum (part of the 42 Network) that introduces you to the fundamentals of virtualization, security, and server configuration.

The objective is to set up a secure virtual machine using Debian or Rocky Linux, implementing strict password policies, service configurations, and network security standards — all without a graphical interface.

Key Objectives

Learn how to install and configure a Linux distribution in a virtualized environment.

Understand user privilege management, security hardening, and firewall configuration.

Implement and manage LVM partitions.

Automate system monitoring through a custom Bash script.

Features

🧩 Custom Virtual Machine Setup

Debian or Rocky Linux OS installation

Logical Volume Manager (LVM) partitioning

🔐 Security Hardening

Password policy enforcement via PAM

Strict sudo permissions and logging

SSH configuration with disabled root login and custom port

Active firewall (UFW / Firewalld)

⚙️ User Management

Dedicated user with sudo privileges

Proper group assignments for access control

📊 Monitoring Script (monitoring.sh)

Displays real-time system information every 10 minutes using wall

Includes CPU, memory, and disk stats, plus user and process counts

System Requirements
Requirement	Description
Virtualization Software	VirtualBox or UTM
OS	Debian / Rocky Linux
RAM	≥ 2 GB
Storage	≥ 20 GB
Tools	SSH, UFW / Firewalld, Cron
Getting Started
🏗️ Installation Steps

Download ISO

Get Debian or Rocky Linux from their official sites.

Create the Virtual Machine

Name: Born2beroot

Type: Linux (64-bit)

Storage: 20 GB (LVM recommended)

RAM: 2048 MB

Install the OS

Use manual partitioning to configure LVM.

Create a non-root user with administrative privileges.

Install only essential system packages (no GUI).

🔧 Post-Installation Configuration

Configure Sudo

Install and restrict sudo access to specific users.

Set Password Policy

Edit /etc/login.defs and /etc/security/pwquality.conf.

Firewall Setup

sudo ufw enable  
sudo ufw allow 4242/tcp  
sudo ufw status  


SSH Setup

Edit /etc/ssh/sshd_config:

Port 4242  
PermitRootLogin no  


Restart SSH service:

sudo systemctl restart ssh  

Monitoring Script

File: monitoring.sh
Purpose: Displays system metrics every 10 minutes.

Example Output
#Architecture: Linux 5.10.0-23-amd64 x86_64  
#CPU physical : 1  
#vCPU : 2  
#Memory Usage: 512/2048MB (25%)  
#Disk Usage: 8/20GB (40%)  
#CPU load: 12.5%  
#Last boot: 2025-10-04 09:42  
#LVM use: yes  
#Connections TCP : 3 ESTABLISHED  
#User log: 1  
#Network: IP 10.0.2.15 (eth0)  
#Sudo : 5 cmd  


Set up as a cron job:

sudo crontab -e  
*/10 * * * * /path/to/monitoring.sh  

Project Structure
File / Directory	Description
monitoring.sh	System monitoring script
/etc/sudoers.d/	Custom sudo configurations
/etc/security/	Password policy settings
/etc/ssh/sshd_config	SSH configuration
/etc/fstab	Filesystem and LVM mount setup
Testing
🔍 Security Checks

Password Expiration

sudo chage -l <username>  


Firewall Status

sudo ufw status  


SSH Access

ssh <user>@<ip> -p 4242  

🧪 Monitoring Verification
bash monitoring.sh  

Evaluation Checklist

✅ Correct OS Installation (Debian/Rocky)
✅ LVM Partitioning Configured
✅ Password Policy Enforced
✅ Firewall and SSH Configured
✅ Monitoring Script Working

Contributions

This repository is for educational purposes only as part of the 1337 School curriculum.
You’re encouraged to fork it for personal exploration, but no external contributions are accepted.

Author

Developed by mokatfi as part of the Born2beroot project at 1337 School, a member of the 42 Network.

License

This project is for academic and educational use only.
Reproduction, redistribution, or plagiarism is strictly prohibited under 1337 School regulations.
