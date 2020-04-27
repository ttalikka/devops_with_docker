## Part 1

### 1.1 Getting started

```
 ttalikka@apro13-5XHV2F  ~/devops_with_docker   master  docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES
e164c07ad49e        nginx               "nginx -g 'daemon of…"   4 minutes ago       Exited (0) 4 minutes ago                       frosty_allen
a4adff79670b        nginx               "nginx -g 'daemon of…"   4 minutes ago       Exited (0) 4 minutes ago                       thirsty_maxwell
dc736d0a12aa        nginx               "nginx -g 'daemon of…"   6 minutes ago       Up 6 minutes               80/tcp              reverent_mcnulty
```

### 1.2 Cleanup

```
 ttalikka@apro13-5XHV2F  ~/devops_with_docker   master  docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
 ttalikka@apro13-5XHV2F  ~/devops_with_docker   master  docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```


### 1.3 Hello Docker Hub

```
 ttalikka@apro13-5XHV2F  ~/devops_with_docker   master  docker run -it devopsdockeruh/pull_exercise
Unable to find image 'devopsdockeruh/pull_exercise:latest' locally
latest: Pulling from devopsdockeruh/pull_exercise
8e402f1a9c57: Pull complete
5e2195587d10: Pull complete
6f595b2fc66d: Pull complete
165f32bf4e94: Pull complete
67c4f504c224: Pull complete
Digest: sha256:7c0635934049afb9ca0481fb6a58b16100f990a0d62c8665b9cfb5c9ada8a99f
Status: Downloaded newer image for devopsdockeruh/pull_exercise:latest
Give me the password: basics
You found the correct password. Secret message is:
"This is the secret message"
```
