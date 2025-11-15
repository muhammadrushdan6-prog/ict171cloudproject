# ICT171 Cloud Project — Cybersecurity Blog Platform

**Student:** Mohammad Rushdan  
**Student ID:** 35415212  
**Project Title:** Cybersecurity Blog Website  
**Hosting Model:** IaaS (Amazon EC2)  
**Platform:** Ubuntu Server on EC2  

## Project Summary
This project implements a Cybersecurity Blog hosted on an Amazon EC2 instance running Ubuntu. The goal is to deploy a simple, secure and scalable blog website on a manually configured cloud VM demonstrating core IaaS concepts such as server setup, networking, DNS configuration and service deployment.

The project highlights:
- Full control of the server stack  
- Secure deployment of a blog platform  
- High availability and scalability using EC2  
- Manual configuration (not pre-built images)  
- Documentation via GitHub  
- A full video walkthrough

## Why IaaS (Amazon EC2)?
Based on a TCO and feature comparison with SaaS (e.g., Bluehost), EC2 is recommended due to:

- **Scalability & Flexibility:** Easily adjustable compute power  
- **Security Control:** Customizable firewalls, OS hardening, SSL  
- **Performance:** Tunable resources for high reliability  
- **Long-term benefits:** Better alignment with a growing blog platform  

Even though SaaS is cheaper short-term, IaaS offers significantly more control and adaptability.

## Planned Technical Setup
- **Cloud Provider:** Amazon AWS (EC2)  
- **OS:** Ubuntu Server 22.04 LTS  
- **Web Server:** Nginx or Apache (final choice will be made during setup)  
- **Application:** Basic blog webpage (HTML/CSS or simple CMS)  
- **Public IP:** (to be added after EC2 setup)  
- **Domain Name:** (optional – can be added later)  
- **Security Features:** UFW firewall, SSH access, HTTPS via Certbot  
- **Automation:** A simple `deployment.sh` script  
- **Documentation:** GitHub repo with step-by-step logs  
- **Video Demonstration:** Full walkthrough of setup and configuration

## Milestones
- [ ] Create GitHub repo & upload Step 1 documentation  
- [ ] Launch EC2 instance & reserve elastic IP  
- [ ] SSH into server & configure security  
- [ ] Install web server & deploy blog  
- [ ] Set up DNS (optional)  
- [ ] Enable HTTPS  
- [ ] Write and commit automation script  
- [ ] Record final video  
- [ ] Produce final PDF for submission
