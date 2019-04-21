Docker LAMP nginx + php-fpm + mysql
===================================

## Install Docker and docker-compose

See doc: https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/

```bash
sudo usermod -aG docker ${USER}
sudo reboot
```

## clone project

```bash
git clone https://github.com/majidlahmidi/docker-nginx-php-fpm-mysql.git && cd docker-nginx-php-fpm-mysql
```

## edit .env file and customize your apps

```bash
vim .env
```

## vhost : docker/apache/sites-enabled/site.conf
## custom php config : docker/php/custom-php.ini
## custom mysql config : docker/db/custom.cnf

### For security reason mysql dont start if docker/db/custom.cnf have not the right chmod :

```bash
sudo chmod 644 docker/db/custom.cnf
```

## start containers

```bash
make dup  (docker-compose up)
```
### OR with -d  (daemon) option

```bash
make dupd (docker-compose up -d)
```

## Connect to a nginx container

```bash
docker-compose exec web bash
```

## See Makefile for alias command
### Example :

```bash
make bash
```
is alias of 

```bash
docker-compose exec web bash
```

You are done!

Visit: http://localhost:8088

Enjoy :-)
