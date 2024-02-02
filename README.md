# EC2 Deployment Guide for Notes App

## Step 1: Set Up EC2 Instance
- Launch an EC2 instance on AWS.

## Step 2: Clone Code and Build
- SSH into the EC2 instance.
- Clone the code repository.
- Install Docker: `sudo apt-get install docker` (for Ubuntu).
- Build the Docker image: `docker build -t notes-app .`

## Step 3: Run Docker Container
- Start the container: `docker run -d -p 8000:8000 notes-app:latest`

## Step 4: Implement Nginx Reverse Proxy
- SSH into the EC2 instance.
- Edit Nginx default file: `sudo nano /etc/nginx/sites-enabled/default`
- Add `proxy_pass http://127.0.0.1:8000;` under the root location.
- Save and exit.

## Step 5: Restart Nginx
- Restart Nginx: `sudo systemctl restart nginx`

## Step 6: Access App through Reverse Proxy
- Visit `EC2-public_ip` in your browser.

## Step 7: Connect Backend via Nginx
- Edit Nginx default file again.
- Add `proxy_pass http://127.0.0.1:8000/api;` under the `/api` location.
- Save and exit.

## Step 8: Restart Nginx
- Restart Nginx: `sudo systemctl restart nginx`

## Step 9: Test Full Application
- Visit `EC2-public_ip/api` in your browser.

## Step 10: Done
Congratulations! The Notes App is deployed on your EC2 instance using Docker and Nginx reverse proxy.