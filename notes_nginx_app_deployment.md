# Steps to Deploy an Application on NGINX

> Reference Git -> [GIT NGINX AWS](https://gist.github.com/piyushgarg-dev/8b14c87c8ff4d626ecbc747b6b9fc57f)

1. Create an AWS Account

2. Create and Launch an EC2 instance

3. Install Node and NPM, using-
    ```
    curl -sL https://deb.nodesource.com/setup_18.x | sudo -E bash -
    
    sudo apt install nodejs

    node --version
    ```

4. Clone the project, say -
    ```
    git clone https://github.com/piyushgargdev-01/short-url-nodejs
    ```

5. Install Process Manager, to keep the app running, 

    ``` 
    sudo npm i pm2 -g
    pm2 start index

    # Other pm2 commands
    pm2 show app
    pm2 status
    pm2 restart app
    pm2 stop app
    pm2 logs (Show log stream)
    pm2 flush (Clear logs)

    # To make sure app starts when reboot
    pm2 startup ubuntu

    ```

6. Install NGINX and configure

    
    > sudo apt install nginx
    

    > sudo nano /etc/nginx/sites-available/default

    Add the following to the location part of the server block

    ```
    server_name yourdomain.com www.yourdomain.com;

    location / {
        proxy_pass http://localhost:8001; 
        #whatever port your app runs on
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection 'upgrade';
        proxy_set_header Host $host;
        proxy_cache_bypass $http_upgrade;
    }
    ```

8. Verify the App and Restart the NGINX 

    // Check NGINX config
    > sudo nginx -t

    // Restart NGINX
    > sudo nginx -s reload

9. Add SSL with LetsEncrypt (Only when you have a Domain Name)
    ```    
    sudo add-apt-repository ppa:certbot/certbot
    sudo apt-get update
    sudo apt-get install python3-certbot-nginx
    sudo certbot --nginx -d yourdomain.com -d www.yourdomain.com
    ```

    // Only valid for 90 days, test the renewal process with

    ```certbot renew --dry-run```