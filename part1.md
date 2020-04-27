## Part 1

### 1.1 Getting started

```shell
 ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker ps -a
CONTAINER ID        IMAGE               COMMAND                  CREATED             STATUS                     PORTS               NAMES
e164c07ad49e        nginx               "nginx -g 'daemon of…"   4 minutes ago       Exited (0) 4 minutes ago                       frosty_allen
a4adff79670b        nginx               "nginx -g 'daemon of…"   4 minutes ago       Exited (0) 4 minutes ago                       thirsty_maxwell
dc736d0a12aa        nginx               "nginx -g 'daemon of…"   6 minutes ago       Up 6 minutes               80/tcp              reverent_mcnulty
```

### 1.2 Cleanup

```shell
 ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker ps -a
CONTAINER ID        IMAGE               COMMAND             CREATED             STATUS              PORTS               NAMES
 ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker images
REPOSITORY          TAG                 IMAGE ID            CREATED             SIZE
```


### 1.3 Hello Docker Hub

```shell
 ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker run -it devopsdockeruh/pull_exercise
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

### 1.4

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker run -d devopsdockeruh/exec_shell_exercise
64a68ef7fd8ae027dd839177cd0acf687023e7711c8e252a92d684caae996cc7
ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker exec -it 64 shell
root@64a68ef7fd8a:/usr/app# tail -f logs.txt
Mon, 27 Apr 2020 07:12:20 GMT
Mon, 27 Apr 2020 07:12:23 GMT
Mon, 27 Apr 2020 07:12:26 GMT
Mon, 27 Apr 2020 07:12:29 GMT
Secret message is:
"Docker is easy"
Mon, 27 Apr 2020 07:12:35 GMT
```

### 1.5

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker run --rm -it --name curl ubuntu sh -c 'apt update; apt install curl -y; echo "Input website:"; read website; echo "Searching.."; sleep 1; curl http://$website;'
... APT snip ...
done.
Input website:
helsinki.fi
Searching..
<!DOCTYPE HTML PUBLIC "-//IETF//DTD HTML 2.0//EN">
<html><head>
<title>301 Moved Permanently</title>
</head><body>
<h1>Moved Permanently</h1>
<p>The document has moved <a href="http://www.helsinki.fi/">here</a>.</p>
</body></html>
```

### 1.6

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker build -t docker-clock 1.6
Sending build context to Docker daemon  2.048kB
Step 1/2 : FROM devopsdockeruh/overwrite_cmd_exercise
---> 3d2b622b1849
Step 2/2 : CMD ["-c"]
---> Running in 84b6da126c95
Removing intermediate container 84b6da126c95
---> 43ca5d34e5f5
Successfully built 43ca5d34e5f5
Successfully tagged docker-clock:latest
ttalikka@apro13-5XHV2F > ~/devops_with_docker >  master > docker run docker-clock
1
2
3
...
```
