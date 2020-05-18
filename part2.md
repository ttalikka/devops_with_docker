## Part 2

### 2.1

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.1 > master > cat docker-compose.yml
version: '3.5'

services:
 first_volume_exercise:
   image: devopsdockeruh/first_volume_exercise
   volumes:
     - ./logs.txt:/usr/app/logs.txt
   container_name: first_vol

ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.1 > master > cat logs.txt
Mon, 11 May 2020 07:22:17 GMT
Mon, 11 May 2020 07:22:20 GMT
```

### 2.2

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.2 > master > docker-compose up -d
...

ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.2 > master > curl localhost:80
Ports configured correctly!!

ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.2 > master > cat docker-compose.yml
version: '3.5'

services:
 ports_exercise:
   image: devopsdockeruh/ports_exercise
   container_name: ports
   ports:
     - 80:80
```

### 2.3

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.3 > master ● > cat docker-compose.yml
version: '3.5'

services:
 frontend:
   build: ../1.10
   ports:
     - 5000:5000
 backend:
   build: ../1.11
   ports:
     - 8000:8000
```

### 2.4

```shell
 ttalikka@apro13-5XHV2F > ~/devops_with_docker/scaling-exercise > master > docker-compose up --scale compute=3
```

### 2.5

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.5 > master > cat docker-compose.yml
version: '3.5'

services:
 frontend:
   build: ../1.10
   ports:
     - 5000:5000
 backend:
   build: ../1.11
   ports:
     - 8000:8000
   environment:
     - REDIS=redis
 redis:
   image: redis:latest
   ports:
     - 6379:6379
```

### 2.6

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.6 > master > cat docker-compose.yml
version: '3.5'

services:
  frontend:
    build: ../1.10
    ports:
      - 5000:5000
  backend:
    build: ../1.11
    ports:
      - 8000:8000
    environment:
      REDIS: redis
      DB_USERNAME: admin
      DB_PASSWORD: testi123
      DB_NAME: devops_with_docker
      DB_HOST: postgres
    depends_on:
      - postgres
  redis:
    image: redis:latest
    ports:
      - 6379:6379
  postgres:
    image: postgres:latest
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: testi123
      POSTGRES_USER: admin
      POSTGRES_DB: devops_with_docker
    volumes:
      - database:/var/lib/postgresql/data

volumes:
  database:
```

### 2.7

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.7 > master > cat docker-compose.yml
version: '3.5'

services:
 frontend:
   build: ./ml-kurkkumopo-frontend
   ports:
     - 3000:3000

 backend:
   build: ./ml-kurkkumopo-backend
   volumes:
     - model:/src/model
   ports:
     - 5000:5000

 training:
   build: ./ml-kurkkumopo-training
   volumes:
     - model:/src/model
     - images:/src/imgs

volumes:
 model:
 images:
```

### 2.8

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.8 > master > cat docker-compose.yml
version: '3.5'

services:

  frontend:
    build: ../1.10
    ports:
      - 5000:5000

  backend:
    build: ../1.11
    ports:
      - 8000:8000
    environment:
      REDIS: redis
      DB_USERNAME: admin
      DB_PASSWORD: testi123
      DB_NAME: devops_with_docker
      DB_HOST: postgres
    depends_on:
      - postgres

  redis:
    image: redis:latest
    ports:
      - 6379:6379

  postgres:
    image: postgres:latest
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: testi123
      POSTGRES_USER: admin
      POSTGRES_DB: devops_with_docker
    volumes:
      - database:/var/lib/postgresql/data

  nginx:
    image: nginx:latest
    ports:
      - 80:80
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf

volumes:
  database:
```

### 2.9

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.9 > master > cat docker-compose.yml
version: '3.5'

services:

 frontend:
   build: ../1.10
   ports:
     - 5000:5000

 backend:
   build: ../1.11
   ports:
     - 8000:8000
   environment:
     REDIS: redis
     DB_USERNAME: admin
     DB_PASSWORD: testi123
     DB_NAME: devops_with_docker
     DB_HOST: postgres
   depends_on:
     - postgres

 redis:
   image: redis:latest
   ports:
     - 6379:6379
   volumes:
     - ./redis:/data

 postgres:
   image: postgres:latest
   restart: unless-stopped
   environment:
     POSTGRES_PASSWORD: testi123
     POSTGRES_USER: admin
     POSTGRES_DB: devops_with_docker
   volumes:
     - ./database:/var/lib/postgresql/data
```

### 2.10

Changed ENV API_URL in frontend Dockerfile from http://localhost:8000 to http://localhost/api/

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.10 > master > cat docker-compose.yml
version: '3.5'

services:

  frontend:
    build: ../1.10
    ports:
      - 5000:5000

  backend:
    build: ../1.11
    ports:
      - 8000:8000
    environment:
      REDIS: redis
      DB_USERNAME: admin
      DB_PASSWORD: testi123
      DB_NAME: devops_with_docker
      DB_HOST: postgres
    depends_on:
      - postgres

  redis:
    image: redis:latest
    ports:
      - 6379:6379

  postgres:
    image: postgres:latest
    restart: unless-stopped
    environment:
      POSTGRES_PASSWORD: testi123
      POSTGRES_USER: admin
      POSTGRES_DB: devops_with_docker
    volumes:
      - database:/var/lib/postgresql/data

  nginx:
    image: nginx:latest
    ports:
      - 80:80
    volumes:
      - ./nginx.conf:/etc/nginx/nginx.conf
    depends_on:
      - backend

volumes:
  database:

ttalikka@apro13-5XHV2F > ~/devops_with_docker/2.10 > master > cat ../1.10/Dockerfile
  FROM ubuntu:latest

  COPY frontend-example-docker frontend-example
  WORKDIR /frontend-example
  EXPOSE 5000

  RUN apt-get update && apt-get install -y curl
  RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
  RUN apt-get update && apt-get install -y nodejs
  RUN node -v && npm -v
  ENV API_URL=http://localhost/api/
  RUN npm install
  CMD npm start

talikka@apro13-5XHV2F > ~/devops_with_docker/2.10 > master > cat ../1.11/Dockerfile
  FROM ubuntu:latest

  COPY backend-example-docker backend-example
  WORKDIR /backend-example
  EXPOSE 8000

  RUN apt-get update && apt-get install -y curl
  RUN curl -sL https://deb.nodesource.com/setup_10.x | bash
  RUN apt-get update && apt-get install -y nodejs
  RUN node -v && npm -v
  ENV FRONT_URL=http://localhost:5000
  RUN npm install
  CMD npm start
```
