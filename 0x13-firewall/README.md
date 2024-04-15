# Firewall Documentation

## Introduction
This document provides an overview of the firewall setup, configuration, and usage.

## Table of Contents
1. [Overview](#overview)
2. [UFW](#Setting Up Firewall with UFW)
3. [Troubleshooting](#troubleshooting)

## Overview
The firewall is a security measure designed to control incoming and outgoing network traffic based on predetermined security rules.

## Setting Up Firewall with UFW

Ensure that you have administrative privileges and access to a terminal.

## Installation

If UFW is not installed, you can install it using the package manager:

```bash
sudo apt-get -y update
sudo apt-get -y install ufw
sudo ufw disable # to disable ufq
sudo ufw default deny incoming # to deny incoming traffic
sudo ufw default allow outgoing # to allow outgoing traffic
sudo systemctl stop ufw # to stop ufw
sudo ufw allow 22/tcp #to allow port 22 for ssh connecctions
sudo ufw allow 443/tcp # to allow https connections
sudo ufw allow 80/tcp # to allow http connections
sudo ufw enable
```

## Troubleshooting
If you encounter any issues with the firewall, refer to the following troubleshooting steps:
- Check list of active connections on server: `netstat -lpn`
- Check for ports being listen to on Nginx server: `grep listen /etc/nginx/sites-enabled/default`
- Check the firewall status: `sudo ufw status`
- Ensure that the configuration file is correctly set up.
- Restart the firewall service: `sudo ufw enable`

## Port Forwarding using UFW
Firewalls can not only filter requests, they can also forward them.

Requirements:
Configuring a server so that its firewall redirects port 8080/TCP to port 80/TCP using ufw.
Run the following commands:
```bash
sudo vi /etc/ufw/before.rules #open the ufw config file (before.rules)
sudo ufw allow 8080 #to allow port 8080
sudo service ufw restart #to restart ufw for the config to be applied
sudo ufw enable #enter y to proceed operation when prompted
```
