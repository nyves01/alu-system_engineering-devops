# Web Server Setup

This folder contains scripts and configuration for setting up a basic web server on Ubuntu using **Nginx**.

## Project Overview

The purpose of this project is to configure an Ubuntu server to serve HTML content using Nginx. The setup should be automated using a Bash script.

---

## Requirements

- Ubuntu 16.04/18.04/20.04 LTS server
- Nginx installed and running
- Nginx should listen on port `80`
- When requesting the root `/` using `curl`, the page should contain the string:

