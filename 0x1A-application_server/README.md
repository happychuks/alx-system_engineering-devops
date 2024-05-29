Solution to Application Server project

For task 0 - 5
- configure the nginx config file
```bash
sudo vi /etc/nginx/site-available/<configFileName>
```

```bash
# configurations
# Configures Nginx to serve the complete AirBnB_clone_v4 application.

server {
    # Listen on port 80
    listen      80 default_server;
    listen      [::]:80 default_server ipv6only=on;

    # Use IP of server as domain name
    server_name 100.26.173.95;

    # Customize HTTP response header
    add_header  X-Served-By 146076-web-01;

    # Serve /airbnb-onepage/ route from AirBnB_clone_v2
    location /airbnb-onepage/ {
        proxy_pass http://127.0.0.1:5000/airbnb-onepage/;
    }

    # Serve /number_odd_or_even/ route on AirBnB_clone_v2
    location ~ /airbnb-dynamic/number_odd_or_even/(\d+)$ {
        proxy_pass http://127.0.0.1:5001/number_odd_or_even/$1;
    }

    # Serve API on AirBnB_clone_v3
    location /api {
        proxy_pass http://127.0.0.1:5002/api;
    }

    # Configure /2-hbnb route of AirBnB_clone_v4 as root location
    location / {
        proxy_pass http://127.0.0.1:5003/2-hbnb;
    }

    # Serve static content for AirBnB_clone_v4
    location /static {
        proxy_pass http://127.0.0.1:5003;
    }

    # 404 error page
    error_page 404 /404.html;
    location /404 {
        root /var/www/html;
        internal;
    }
}
```

## For gunicorn.service
Create a gunicorn config file using:

```bash
sudo vi /etc/systemd/system/gunicorn.service
```

```bash 
#Gunicorn service config
[Unit]
Description=Gunicorn instance to serve application
After=network.target

[Service]
User=ubuntu
Group=ubuntu
WorkingDirectory=/home/ubuntu/AirBnB_clone_v4
Environment="HBNB_MYSQL_USER=hbnb_dev"
Environment="HBNB_MYSQL_PWD=hbnb_dev_pwd"
Environment="HBNB_MYSQL_HOST=localhost"
Environment="HBNB_MYSQL_DB=hbnb_dev_db"
Environment="HBNB_TYPE_STORAGE=db"
ExecStart=/home/ubuntu/.local/bin/gunicorn --workers 3 --bind 0.0.0.0:5003 --error-logfile /tmp/airbnb-error.log --access-logfile /tmp/airbnb-access.log  web_dynamic.2-hbnb:app
ExecReload=/bin/kill -s HUP $MAINPID
KillMode=mixed
TimeoutStopSec=5
PrivateTmp=true
Restart=always

[Install]
WantedBy=multi-user.target
```
- To Enable the gunicorn service, run the following commands:
```sudo systemctl enable gunicorn``` and ```sudo systemctl start gunicorn``` 
If successful, you would get `#Created symlink /etc/systemd/system/multi-user.target.wants/gunicorn.service → /etc/systemd/system/gunicorn.service`

