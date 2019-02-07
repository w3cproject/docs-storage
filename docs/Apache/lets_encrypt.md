##  How To Secure Apache with Let's Encrypt on Ubuntu 18.04

### Step 1 — Installing Certbot

```
sudo apt install python-certbot-apache

sudo add-apt-repository ppa:certbot/certbot
```

### Step 2 — Set Up the SSL Certificate

```
sudo nano /etc/apache2/sites-available/example.com.conf

Find the existing ServerName line. It should look like this:

ServerName example.com;

sudo systemctl reload apache2
```

### Step 3 — Allowing HTTPS Through the Firewall

```
sudo ufw status
```

It will probably look like this, meaning that only HTTP traffic is allowed to the web server:

```
Output
Status: active

To                         Action      From
--                         ------      ----
OpenSSH                    ALLOW       Anywhere                  
Apache                     ALLOW       Anywhere                  
OpenSSH (v6)               ALLOW       Anywhere (v6)             
Apache (v6)                ALLOW       Anywhere (v6)
```

To additionally let in HTTPS traffic, allow the Apache Full profile and delete the redundant Apache profile allowance:

```
sudo ufw allow 'Apache Full'
sudo ufw delete allow 'Apache'
```

### Step 4 — Obtaining an SSL Certificate

```
sudo certbot --apache -d example.com -d www.example.com
```

This runs certbot with the --apache plugin, using -d to specify the names you'd like the certificate to be valid for.

### Step 5 — Verifying Certbot Auto-Renewal

Let's Encrypt's certificates are only valid for ninety days. This is to encourage users to automate their certificate renewal process. The `certbot` package we installed takes care of this for us by adding a renew script to `/etc/cron.d`. This script runs twice a day and will automatically renew any certificate that's within thirty days of expiration.

To test the renewal process, you can do a dry run with `certbot`:

```
sudo certbot renew --dry-run
```

[Source digitalocean](https://www.digitalocean.com/community/tutorials/how-to-secure-apache-with-let-s-encrypt-on-ubuntu-18-04)