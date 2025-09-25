# Demo with PHP + Laravel


## Steps to run ?

Start web server with NGINX
```
docker compose up -d --build web app
```

Create Laravel 4.2 project
```
docker compose run --rm composer create-project laravel/laravel:12 .
```

Create all containers
```
docker compose up -d
docker compose up -d
```

List of urls
* http://localhost:8080
* http://localhost:8080/hello