# Solution to HTTPS_SSL Project

-	Task 0[0-world_wide_web]: Add the sub-domains and their respective IP address on the domain management portal (.tech)

-	Task 1[1-haproxy_ssl_termination]: 
teps to get your domain serving over HTTPS:

## 1. Generating your SSL Certificate from Certbot:

(I) Install Certbot: 
```bash 
 sudo apt update && apt upgrade 
sudo apt install certbot
``` 

(II) Generate your SSL certificate: 

```bash
sudo service haproxy stop
sudo certbot certonly --standalone -d www.example.tech
```
 
Follow prompts and you'll have your cert ready

## 2. Configuring haproxy with your certificate

(I) Make a combination file of your certificate and private key
```
cd /etc/letsencrypt/live/www.example.tech/
cat fullchain.pem privkey.pem > www.example.tech.pem
```
## Combine your certificate and private key

(II) Add the file in your haproxy.cfg file

  - open /etc/haproxy/haproxy.cfg with a text editor.
  - add the following line in your fronted section in your file: 

	*bind *:443 ssl crt /etc/letsencrypt/live/www.example.tech/www.example.tech.pem*

  - lastly, add the following line in the 'global' section of the configuration file: 
 tune.ssl.default-dh-param 2048

3. Restart HAProxy service

```bash
sudo service haproxy restart
```


::: That's it! Your site will now serve https


Ps: If you want to redirect http traffic to https, add the following line in the backend section of the haproxy.cfg file:

redirect scheme https if !{ ssl_fc }
 

