## This is docker-compose with included: ```PHP``` (```7.0```, ```7.1```, ```7.2```, ```7.3```, ```7.4```, ```8.0```, ```8.1```), ```Nginx```, ```MySQL```, ```Redis```, ```Memcached```, ```RabbitMQ```

### How to use?
1. Clone this repository: ```git clone https://github.com/vityachis/docker-compose.git```
2. Copy ```docker-compose.yml``` and ```docker``` to your project root directory
3. Rename the folder with required PHP version to ```php``` (in ```docker``` folder)
4. Delete unnecessary PHP versions from ```docker``` folder
5. Set ENV variables (if need)
6. Configure Xdebug in PhpStorm
7. **ENJOY :)**


### Global ENV variables:
###### Mapping local ports to ports in Docker container (ports for services in Docker container remain default): ```APP_PORT```, ```APP_SECURE_PORT```, ```MYSQL_PORT```, ```REDIS_PORT```, ```RABBITMQ_PORT```, ```RABBITMQ_MANAGEMENT_PORT```

- ```ROOT_PATH``` (default ```/var/www/public```)
<br>

- ```APP_PORT``` (default ```80```)
- ```APP_SECURE_PORT``` (default ```443```)
- ```XDEBUG_PORT``` (default: ```9003```)
- ```XDEBUG_IDEKEY``` (default ```IDEKEY```)
- ```NGINX_HOST``` (default ```app.local```)
<br>

- ```MYSQL_PORT``` (default ```3306```)
- ```DB_DATABASE``` (default ```app```)
- ```DB_USERNAME``` (default ```app```)
- ```DB_PASSWORD``` (default ```app```)
- ```DB_ROOT_USERNAME``` (default ```uroot```)
- ```DB_ROOT_PASSWORD``` (default ```proot```)
<br>

- ```REDIS_PORT``` (default ```6379```)
<br>

- ```RABBITMQ_PORT``` (default ```5672```)
- ```RABBITMQ_MANAGEMENT_PORT``` (default ```15672```)
- ```RABBITMQ_USER``` (default ```guest```)
- ```RABBITMQ_PASS``` (default ```guest```)

### Settings Xdebug for PhpStorm:
1. Preferences
2. PHP:
    - Add new CLI Interpreters:
      - Server: ```Docker```
      - Image name: ```%PROJECT_FOLDER_NAME%_php:latest```
    - Path mappings (or Docker container ```[Host path] -> [Container path]```):
      - ```<Project root> -> /var/www```
    - Xdebug:
      - Debug port: ```${XDEBUG_PORT}```
      - DBGp Proxy: IDE key: ```${XDEBUG_IDEKEY}```; Host: ```host.docker.internal```; Port: ```${XDEBUG_PORT}```
    - Servers:
      - Host: ```${nginx_host}``` (this is **NOT** an environment variable)
      - Port: ```80```
      - Debugger: ```Xdebug```
      - Use path mappings: ```<Project root> -> /var/www```; ```<Root path (where is index.php)> -> ${ROOT_PATH}```
