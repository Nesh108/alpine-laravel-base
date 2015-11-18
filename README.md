# alpine-laravel
Alpine Linux Docker image (~54.3 MB) running Laravel Framework.  Image suitable for running in Tutum/Kubernetes style hosted distributed environments. 

Image is based on [sillelien/base-alpine](https://hub.docker.com/r/sillelien/base-alpine/) base image which incorporates S6 for process management.

## To build

    $ make build

    or

    $ docker build -t yourname/alpine-laravel .

## To run
Map your application to /var/www directory

    $ docker run -d -p 8000:80 -v laravel-app:/var/www yourname/alpine-laravel

## Use with Docker Compose
A docker-compose.yml with this image would look like:

    web:
      image: michaeldim/alpine-linux
      volumes:
        - laravel-app:/var/www
      ports:
        - "80:80"
      links:
        - "mysql:mysql"
    mysql:  
      image: tutum/mysql:5.6
      ports:
        - "3306:3306"
      environment:
        MYSQL_PASS: password
