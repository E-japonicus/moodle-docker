### moodle-docker  

Image for activating moodle  
  
***  
# Installation  
`git clone https://github.com/E-japonicus/moodle-docker.git`  
`cd moodle-docker`  
`docker-compose build`  

  
*** 

# Usage  
Test Environment  
You can use localhost for local use.  
You can start a new instance as follows.
  
`docker-compose up -d`  

You can visit following URL in a browser to get started.  
`http://localhost`

However, in this state, container `/var/www/html` is empty, so you need to place moodle's source code in `moodle-docker/public` on the host.

For ezample when using moodle 3.0.3  
`cd /moodle-docker/public`  
`wget https://download.moodle.org/stable30/moodle-3.0.3.tgz`  
`tar -xzvf moodle-3.0.3.tgz --strip=1`  


## Install moodle

Once moodle source code is downloaded, access `http://localhost`.  
This will automatically access the moodle installation page.  
Please proceed with the setting according to the displayed procedure.  
Please set as following for database setting.  
```
Database host: mdldb  
Database name: moodle  
Database user: mdluser
Database password: mdlpass

```



***  

# Construction

```
moodle-docker
|--Docker-compose.yml  
|--moodle-variables.env  
|--mysql    
|  |--data      
|  |--moodle-mysql.cnf  
|--php5   
|  |--Dockerfile  
|  |--moodle-apache2.conf  
|  |--moodle-php.ini  
|  |--moodledata      
|--public  
```

The database is stored in `/moodle-docker/mysql/data`  
The moodle setting is stored in `/moodle-docker/php5/moodledata`  

***

# Using version  

OS: ubuntu 14.04  
PHP: php5.5.9  
MYSQL: mysql5.5.59  
Apache: apache2  
