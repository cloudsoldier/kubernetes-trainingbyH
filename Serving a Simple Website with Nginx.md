Serving a Simple Website with Nginx on your personal domain

- In this excercise I will show you guys a simple index page or website with nginx web server


Steps
- Create a Linux virtual vm in Azure 
- log on to the VM via Terminal
- To avoid logging as sudo user
  ```
  sudo passwd root
  # type your linux vm password
  # Then
  ssh root@yourvmpublicip
  ```
- Create NSG rule to allow port 80 using Azure portal
- Install Nginx
- Use below commands
- sudo apt update
- sudo apt install nginx -y
- Enable and start Nginx
- sudo systemctl enable nginx
- sudo systemctl start nginx

** Check Status

- systemctl status nginx

** Create your webpage**
- in your terminal
- Go to cd /var/www/html
- create an index.html file
- Use this command sudo vi index.html
- paste this HTML content

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>DevOps Test Page</title>
    <style>
        body {
            font-family: Arial, sans-serif;
            background-color: #f4f4f4;
            text-align: center;
            margin-top: 20%;
        }
        h1 {
            color: #333;
        }
        p {
            color: #555;
        }
    </style>
</head>
<body>
    <h1>🚀 DevOps Deployment Test by Kash</h1>
    <p>If you see this page, your deployment worked! ✅</p>
</body>
</html>
```

At this point, if you go to your **server IP** (e.g., `http://Your public IP from Azure portal`), you’ll already see the page.

## **Step 3: Create an Nginx Configuration File for Your Site**

Instead of editing the **default config**, we create a **new site config**.
this will incorporte with our domain, and my domain is cloudsoldier.co.uk
---

### 1️⃣ Create a config file:

```bash
sudo vi /etc/nginx/sites-available/nginx.yourdomain_name

server {
    listen 80;
    server_name nginx.yourdomain-name which you bought from Godaddy;

    root /var/www/html;
    index index.html;

    location / {
        try_files $uri $uri/ =404;
    }

    access_log /var/log/nginx/nginx.yourdomain_name.access.log;
    error_log /var/log/nginx/nginx.yourdomain_name.log;
}

```
---

What does this mean?
listen 80; → Nginx listens on HTTP port 80.

server_name nginx.cloudsoldier.co.uk; → This config is for your domain.

root /var/www/html; → Where Nginx looks for files.

index index.html; → The default file served.

location / { try_files $uri $uri/ =404; } → Serves the file if it exists; otherwise, returns 404.

access_log / error_log → Where logs will be saved.
