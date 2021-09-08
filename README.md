# py-microservice-webapp-demo

A demo microservice web application examining performance and refactoring.

---

## Instructions Checklist

### Start MySQL container

```sh
docker run -d --name app-db --cpus 0.5 --memory 512m -e MYSQL_USER=adam -e MYSQL_ROOT_PASSWORD=root -e MYSQL_DATABASE=web_app_db --net app-net mysql:5.7
```

### Start Webapp container

```sh
docker run -itd --name web-app-1 -v $PWD:/code --cpus 0.5 --memory 512m -p 8080:8000 --workdir /code --net app-net -e DOCKER_CONTAINER_ID=1 python:3.8
```

### Start Load Testing container

```sh
docker run -itd --name load_tester --cpus 2 --memory 2g --net app-net node:latest
```

### Start Nginx container

```sh
docker run -itd --name load_balancer --cpus 2 --memory 2g --net app-net -p 80:80 --workdir /etc/nginx/conf.d -v $PWD/static:/static nginx:latest
```

### Start Redis container

```sh
docker run -itd --name app-redis --cpus 0.5 --memory 512m --net app-net redis
```

---

## Technologies & Frameworks

- [Django]()
- [Docker]()
- [Gunicorn]()
- [Nginx]()
- [Redis]()
- [MySQL]()
- [Python]()