# AzerothCore Playermap

![Eastern Kingdom](https://raw.githubusercontent.com/azerothcore/playermap/master/img/showcase/eastern_kingdom.png)  
![Outland](https://raw.githubusercontent.com/azerothcore/playermap/master/img/showcase/outland.png)  
![Northrend](https://raw.githubusercontent.com/azerothcore/playermap/master/img/showcase/northrend.png)  

## Overview

This project provides a php based app that shows where all the players/playerbots are in the server. By default AzerothCore saves player position on logout and every 15 minutes.

## Configure

1. Open **config/playermap_config.php** and configure it based on your server setup.  
2. Open **pomm_conf.php** and set the **realmd_id**.  

Done!  

## Setup Instructions

To run this project, you need to install PHP and a web server. Follow the instructions for your operating system:  

### Windows

1. **Install PHP:**  
   - Download PHP for Windows from [PHP's official site](https://windows.php.net/download).  
   - Extract the contents to `C:\php`.  
   - Add `C:\php` to your system's PATH environment variable.  

2. **Install a Web Server (Apache or Nginx):**  
   - **Option 1: Apache**  
     - Download Apache from [Apache Lounge](https://www.apachelounge.com/download/).  
     - Extract the contents and configure `httpd.conf` to integrate PHP:  
       ```
       LoadModule php_module "C:/php/php8apache2_4.dll"  
       AddHandler application/x-httpd-php .php  
       PHPIniDir "C:/php"  
       ```  
     - Set the `DocumentRoot` to your project's directory.  
   - **Option 2: Nginx**  
     - Download Nginx from [Nginx's official site](http://nginx.org/en/download.html).  
     - Configure Nginx to use PHP by editing `nginx.conf`:  
       ```
       location ~ \.php$ {  
           fastcgi_pass 127.0.0.1:9000;  
           fastcgi_index index.php;  
           fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;  
           include fastcgi_params;  
       }  
       ```  

3. **Start the Web Server:**  
   - Run `httpd.exe` for Apache or `nginx.exe` for Nginx.  
   - Open a browser and navigate to `http://localhost` to see your project.  

### macOS

1. **Install PHP:**  
   - Use Homebrew to install PHP:  
     ```
     brew install php  
     ```  

2. **Install a Web Server (Apache or Nginx):**  
   - **Option 1: Apache**  
     - Apache comes pre-installed on macOS. Enable it by running:  
       ```
       sudo apachectl start  
       ```  
     - Configure Apache to use PHP by editing `/etc/apache2/httpd.conf`:  
       ```
       LoadModule php_module /usr/local/opt/php/lib/httpd/modules/libphp.so  
       ```  
     - Set the `DocumentRoot` to your project directory.  
   - **Option 2: Nginx**  
     - Install Nginx using Homebrew:  
       ```
       brew install nginx  
       ```  
     - Configure Nginx as described above in the Windows instructions.  

3. **Start the Web Server:**  
   - For Apache, run:  
     ```
     sudo apachectl restart  
     ```  
   - For Nginx, run:  
     ```
     sudo nginx  
     ```  
   - Open a browser and navigate to `http://localhost` to see your project.  

### Linux (Ubuntu/Debian)

1. **Install PHP and a Web Server:**  
```
sudo apt update
sudo apt install php apache2 libapache2-mod-php
```

2. **Configure Apache to Use PHP:**  
- Edit `/etc/apache2/sites-available/000-default.conf` and set the `DocumentRoot` to your project directory.  

3. **Restart Apache:**
```
sudo systemctl restart apache2
```

4. **Alternative: Using Nginx**  
- Install Nginx and PHP-FPM:  
  ```
  sudo apt install nginx php-fpm  
  ```  
- Configure Nginx to use PHP:  
  ```
  location ~ \.php$ {  
      fastcgi_pass unix:/var/run/php/php-fpm.sock;  
      fastcgi_index index.php;  
      fastcgi_param SCRIPT_FILENAME $document_root$fastcgi_script_name;  
      include fastcgi_params;  
  }  
  ```  
- Restart Nginx:  
  ```
  sudo systemctl restart nginx  
  ```  

5. **Verify Setup:**  
- Open a browser and navigate to `http://localhost` to ensure the project is running.  

## Credits

- Dustin Hendrickson (Fixed 2024)  
- Dmitry Koterov (original author)  
- Helias (old maintainer)  