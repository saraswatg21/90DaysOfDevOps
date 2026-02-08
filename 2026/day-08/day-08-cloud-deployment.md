# Day 08 – Cloud Server Setup: Docker, Nginx & Web Deployment

---

## Commands Used

```bash
# Connect to cloud instance
ssh -i 2501key.pem ubuntu@<public-ip>

# Update system packages
sudo apt update && sudo apt upgrade -y

# Install Docker
sudo apt install docker.io -y
sudo systemctl start docker
sudo systemctl enable docker

# Install Nginx
sudo apt install nginx -y
sudo systemctl status nginx

# Check Nginx logs
sudo tail -n 20 /var/log/nginx/access.log

# Save logs to file
sudo cat /var/log/nginx/access.log > ~/nginx-logs.txt

# Download logs to local machine (run locally)
scp -i 2501key.pem ubuntu@<public-ip>:~/nginx-logs.txt .
```

---

## Challenges Faced

* Unable to access Nginx webpage using the instance IP initially

  * **Solution:** Opened port 80 (HTTP) in the EC2 security group

* Faced issues while downloading logs using `scp`

  * **Solution:** Realized `scp` must be run from the local machine where the `.pem` key exists, not from inside the EC2 instance

---

## What I Learned

* How to launch and connect to a cloud server using SSH
* Installing and managing services like Docker and Nginx on Linux
* Importance of security groups and firewall rules for web access
* How to locate, extract, and download service logs from a server

---

## Why This Matters for DevOps

This exercise teaches core DevOps skills used in real production environments:

* **Cloud infrastructure provisioning** – launching and configuring servers
* **Remote server management** – SSH access, security, permissions
* **Service deployment** – installing and running applications
* **Log management** – accessing and analyzing logs
* **Security** – configuring firewalls and security groups

These are foundational skills for any DevOps engineer.

---


![Nginx screenshot](nginx-webpage.png)
![Nginx logs screenshot](Nginx-screenshot.png)
![ssh screenshot](ssh-screenshot.png)

---


