Serving a Simple Website with Nginx on your personal domain

- In this excercise I will show you guys a simple index page or website with nginx web server
Steps
- Create a Linux virtual vm in Azure 
- log on to the VM
- Install Nginx
- sudo apt update
- sudo apt install nginx -y
- Enable and start Nginx
- sudo systemctl enable nginx
- sudo systemctl start nginx

** Check Status

- systemctl status nginx

** Create your webpage**
- cd /var/www/html
- create an index.html file
- sudo vi index.html
- paste this HTML content

'''
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
    <h1>🚀 DevOps Deployment Test</h1>
    <p>If you see this page, your deployment worked! ✅</p>
</body>
</html>
