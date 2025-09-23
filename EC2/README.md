# EC2 Instance ( )

https://docs.nginx.com/nginx/admin-guide/installing-nginx/installing-nginx-open-source/

1️⃣. Connect to your EC2 Instance
```
ssh -i your-key.pem ubuntu@your-ec2-public-ip
```

**Ubuntu**

2️⃣. Update the system
```
sudo apt update -y
sudo apt upgrade -y
```

3️⃣. Install Nginx
```
sudo apt install nginx -y
```

4️⃣. Start Nginx Service
```
sudo systemctl start nginx
```

5️⃣. Enable Nginx to start on boot
```
sudo systemctl enable nginx
```


6️⃣. Check Nginx Status
```
sudo systemctl status nginx
```

7️⃣. Configure AWS Security Group

Ensure your EC2 instance’s Security Group Inbound Rules allow:

HTTP (port 80)

HTTPS (port 443)


8️⃣. Test in Browser
Open a browser and visit:
```
http://your-ec2-public-ip
```



📍 1. Open the Nginx config file
```
sudo nano /etc/nginx/nginx.conf
```

🧹 2. Clear existing content
In nano:

Hold CTRL + K multiple times to cut all lines (or delete manually).

📋 3. Paste the correct config
```
worker_processes auto;

events {
    worker_connections 1024;
}

http {
    include       mime.types;
    default_type  application/octet-stream;

    sendfile        on;
    keepalive_timeout  65;

    server {
        listen       80;
        server_name  _;

        location / {
            root   /var/www/mywebsite;
            index  index.html;
        }
    }
}
```

💾 4. Save and Exit

Press CTRL + X

Press Y (to save)

Press Enter


🧪 5. Test the Nginx config
```
sudo nginx -t
```


🔁 6. Reload Nginx

```
sudo systemctl reload nginx
```





