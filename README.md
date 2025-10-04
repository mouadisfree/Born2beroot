Born2beroot - Virtual Machine Configuration & System Administration


A project to master Linux system setup, security, and administration

Overview

Born2beroot is a foundational project from the 1337 School curriculum (part of the 42 Network) designed to introduce students to system administration and virtual machine management.

The goal of this project is to create and configure a secure virtual machine running Debian or Rocky Linux, applying strict security rules, partitions, and user privileges to reflect real-world system administration practices.

Key Objectives

Learn how to install and configure a Linux operating system on a virtual machine.

Understand the basics of system security and privilege management.

Set up partitions, manage users and groups, and configure essential services.

Implement strong password policies and monitoring tools for system integrity.

Features

Operating System: Debian or Rocky Linux (user’s choice).

Security Enhancements:

Strong password policies enforced via PAM.

Configured sudo with restricted permissions and logging.

Firewall enabled using UFW or Firewalld.

SSH configured for secure remote access (port modification, no root login).

Partition Scheme: Custom partitioning layout using LVM.

User Management:

Separate user with sudo privileges.

Proper group configuration for permission management.

Monitoring Script:

A Bash script (monitoring.sh) displaying real-time system information every 10 minutes via wall.

System Requirements

To complete this project, you’ll need:

VirtualBox or UTM installed on your host machine.

A Debian or Rocky Linux ISO image.

Minimum of 2 GB RAM and 20 GB disk space allocated to the VM.

Getting Started
1. Setting Up the Virtual Machine

Download the latest Debian or Rocky Linux ISO.

Create a new virtual machine in VirtualBox:

Name: Born2beroot

Type: Linux

Version: Debian (64-bit) or Rocky (64-bit)

Memory: 2048 MB

Storage: 20 GB (LVM partitioning recommended)

Boot from the ISO and start the installation process.

2. System Configuration

During installation:

Create a hostname of your choice (e.g., mokatfi42).

Configure a non-root user with administrative privileges.

Set up LVM partitions for /, /home, /var, and /swap.

Choose only essential system utilities (no GUI).

After installation, configure the following:

Enable and configure sudo.

Set password policies in /etc/login.defs and /etc/security/pwquality.conf.

Configure the UFW or Firewalld firewall.

Enable SSH (port 4242 recommended) and disable root SSH login.

Monitoring Script

Create a Bash script monitoring.sh that displays system information every 10 minutes using the wall command.

Example Information Displayed:

Architecture and kernel version

CPU and memory usage

Disk usage and LVM status

Number of active users and processes

Network IP and MAC address

Number of executed sudo commands

Run it as a cron job:

sudo crontab -e  
*/10 * * * * /path/to/monitoring.sh  

Project Structure
File / Folder	Description
monitoring.sh	Bash script for system monitoring.
/etc/sudoers.d/	Contains custom sudo configurations.
/etc/security/	Password and login policy files.
/etc/ssh/sshd_config	SSH configuration file (port and access control).
/etc/fstab	Filesystem mount configuration with LVM.
Testing
Verify Security Configurations

Check password policy:

sudo chage -l <username>  


Verify firewall status:

sudo ufw status  


Test SSH connection:

ssh <user>@<IP> -p 4242  

Validate Monitoring Script

Manually trigger the script to ensure correct output:

bash monitoring.sh  

Evaluation Checklist

 Proper installation of Debian/Rocky Linux

 Correct LVM partitioning setup

 Strong password and sudo policies

 Firewall enabled and SSH configured

 Monitoring script outputs accurate system data

Contributions

This project is not open for external contributions, as it forms part of the 1337/42 School curriculum. However, feel free to fork and adapt it for personal experimentation and learning.

Author

Developed by mokatfi as part of the 1337 School system administration curriculum, under the 42 Network.

License

This project is created for educational purposes only and follows the 1337 School policies. Redistribution, plagiarism, or submission under another student’s name is strictly prohibited.
