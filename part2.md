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
