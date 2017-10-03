# Dockerized PHP 7 enviroment
## Technology included

* [Nginx](http://nginx.org/)
* [PostgreSQL](https://www.postgresql.org/)
* [PHP 7](http://php.net/)

##Installation
Clone the repository.
Change directory into the cloned project.
Run the following command.
```sh
$ docker-compose up -d
```
###Composer
```sh
$ docker exec -it <php container name> composer
```