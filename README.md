# ICT171 Cloud Project — Cybersecurity Blog Platform

**Student:** Mohammad Rushdan  
**Student ID:** 35415212  
**Domain:** https://cyberblog.site  
**Public IP (Elastic IP):** 13.202.4.155  
**Course:** ICT171  
**Hosting Model:** IaaS (Amazon EC2)  
**Operating System:** Ubuntu Server 22.04 LTS  

---

# Project Summary
This project demonstrates the deployment of a Cybersecurity Blog website on an Amazon EC2 Ubuntu instance using the IaaS cloud model.  
The goal is to show competency in cloud provisioning, server management, DNS configuration, security hardening, web server deployment, automation scripting, and HTTPS setup.

The website is fully hosted at:

**https://cyberblog.site**

---

#Why IaaS (Amazon EC2)?
A comparison of IaaS (EC2) versus SaaS (Bluehost) showed that:

- IaaS offers **greater flexibility and scalability**  
- Full **security control**  
- Customizability of the **Linux server environment**  
- Better alignment with cybersecurity practices  
- Allows hands-on cloud configuration (valuable for learning)

Even though SaaS is cheaper in the long term, EC2 offers significantly **greater control and customization**, making it ideal for this project.

---

# Step 1 — Project Planning
**Chosen Setup:**
- Cloud Provider: Amazon AWS  
- Instance Type: t3.micro (Free Tier)  
- Storage: 8GB gp3  
- OS: Ubuntu 22.04 LTS  
- Web Server: Nginx  
- Domain Name: cyberblog.site  
- SSL: Enabled using Certbot  
- Custom Website: Modern Cybersecurity Blog  

---

#Step 2 — EC2 Instance Creation
**Instance Configuration:**
```
Instance Name: ICT171-Blog-Server
AMI: Ubuntu Server 22.04 LTS
Instance Type: t3.micro
Storage: 8GB gp3
Elastic IP: 13.202.4.155
Security Groups:
 - SSH (22)    → 0.0.0.0/0
 - HTTP (80)   → 0.0.0.0/0
 - HTTPS (443) → 0.0.0.0/0
```

Screenshots Included in PDF:
- AMI selection  
- Instance type  
- Security groups  
- EC2 instance overview  
- Elastic IP allocation  

---

#Step 3 — SSH Connection to EC2

SSH command used from macOS:

```
ssh -i "~/Downloads/aws-key.pem" ubuntu@13.202.4.155
```

Initial setup & updates:
```
sudo apt update && sudo apt upgrade -y
```

---

# Step 4 — Server Hardening (Security)

**Created new admin user:**
```
sudo adduser deployer
sudo usermod -aG sudo deployer
```

**Configured UFW firewall:**
```
sudo ufw allow OpenSSH
sudo ufw allow 80
sudo ufw allow 443
sudo ufw enable
sudo ufw status
```

This ensures only SSH, HTTP, and HTTPS are accessible.

---

#Step 5 — Nginx Installation & Configuration

Installed Nginx:
```
sudo apt install nginx -y
sudo systemctl enable nginx
sudo systemctl start nginx
sudo systemctl status nginx
```

Replaced default web page with custom HTML.

Browser confirmed website loads correctly.

---

#Step 6 — Cybersecurity Blog Deployment

Replaced the default Nginx page:

```
cd /var/www/html
sudo rm index.html
sudo nano index.html
```

Added a **fully custom, modern Cybersecurity Blog** with multiple posts, CSS styling, and responsive layout.

Website live at:
**https://cyberblog.site**

Screenshots included in PDF:
- Editing index.html  
- Final website appearance  

---

#Step 7 — DNS Configuration (Domain: cyberblog.site)

**DNS Records Added:**
```
A   @     13.202.4.155
A   www   13.202.4.155
```

**Updated Nginx server block:**
```
server_name cyberblog.site www.cyberblog.site;
```

Reloaded Nginx:
```
sudo systemctl reload nginx
```

DNS propagated successfully and domain resolved to EC2.

---

#Step 8 — HTTPS (SSL Certificate)

Installed Certbot:
```
sudo apt install certbot python3-certbot-nginx -y
```

Generated certificate:
```
sudo certbot --nginx -d cyberblog.site -d www.cyberblog.site
```

Enabled automatic redirection to HTTPS.

Result:  
**https://cyberblog.site now shows a secure SSL padlock**

---

#Step 9 — Deployment Automation Script

Created script folder:
```
mkdir ~/scripts
```

Created deployment script:
```
sudo nano ~/scripts/deployment.sh
```

**Script contents:**
```bash
#!/bin/bash
echo "Starting deployment..."
WEB_DIR="/var/www/html"
sudo rsync -av --delete ~/blog_content/ $WEB_DIR/
sudo chown -R www-data:www-data $WEB_DIR
sudo chmod -R 755 $WEB_DIR
sudo systemctl restart nginx
echo "Deployment complete! Website updated successfully."
```

Made executable:
```
sudo chmod +x ~/scripts/deployment.sh
```

Creates automated deployment pipeline for updating site content.


#Final Summary
This project demonstrates:

✔ Cloud provisioning  
✔ Server hardening  
✔ Web server configuration  
✔ DNS + domain integration  
✔ SSL/HTTPS security  
✔ Automation scripting  
✔ Documentation + version control  

Final website:
https://cyberblog.site

---

# References
- AWS EC2 Documentation  
- Nginx Documentation  
- Certbot / Let’s Encrypt Docs  
