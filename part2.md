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
