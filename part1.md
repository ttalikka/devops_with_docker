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

### 1.7

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > docker build -t curler 1.7
Sending build context to Docker daemon  3.072kB
Step 1/5 : FROM ubuntu:16.04
---> 005d2078bdfa
Step 2/5 : RUN apt-get update && apt-get install -y curl
---> Using cache
---> 6cb2fc1754fe
Step 3/5 : COPY curler.sh .
---> ed95884d7b9b
Step 4/5 : RUN chmod +x ./curler.sh
---> Running in 45a594ad689c
Removing intermediate container 45a594ad689c
---> cd08b6a0f179
Step 5/5 : CMD ["./curler.sh"]
---> Running in b756dea55929
Removing intermediate container b756dea55929
---> 2b1a5e8b7179
Successfully built 2b1a5e8b7179
Successfully tagged curler:latest

ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > docker run --rm -it curler
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

### 1.8

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > touch 1.8/logs.txt

 ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > docker run -v $(pwd)/1.8/logs.txt:/usr/app/logs.txt devopsdockeruh/first_volume_exercise
(node:1) ExperimentalWarning: The fs.promises API is experimental
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
Wrote to file /usr/app/logs.txt
^CClosing file

 ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > cat 1.8/logs.txt
Mon, 27 Apr 2020 11:21:07 GMT
Mon, 27 Apr 2020 11:21:10 GMT
Mon, 27 Apr 2020 11:21:13 GMT
Mon, 27 Apr 2020 11:21:16 GMT
Secret message is:
"Volume bind mount is easy"
Mon, 27 Apr 2020 11:21:22 GMT
Mon, 27 Apr 2020 11:21:25 GMT
```

### 1.9

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > docker run -d -p 80 devopsdockeruh/ports_exercise
55d3c89af01f5c00df5855f239451cf89df3d4faf3a669876b8c79bc932cd3c0

 ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > docker port 55
80/tcp -> 0.0.0.0:32768

 ttalikka@apro13-5XHV2F > ~/devops_with_docker > master > curl localhost:32768
Ports configured correctly!!%
```

### 1.10

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.10 > master > docker build -t frontend-example .
Sending build context to Docker daemon  910.3kB
...
Successfully built 4603b88a0a9d
Successfully tagged frontend-example:latest

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.10 > master > docker run -p 5000:5000 frontend-example

> frontend-example-docker@1.0.0 start /frontend-example
> webpack --mode production && serve -s -l 5000 dist
...
INFO: Accepting connections at http://localhost:5000

```

### 1.11

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.11 > master > docker build -t backend-example .
Sending build context to Docker daemon  371.2kB
...
Successfully built 3c71ee9989d4
Successfully tagged backend-example:latest

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.11 > master > touch logs.txt

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.11 > master > docker run -p 8000:8000 -v $(pwd)/logs.txt:/backend-example/logs.txt backend-example

> backend-example-docker@1.0.0 start /backend-example
> cross-env NODE_ENV=production node index.js

Browserslist: caniuse-lite is outdated. Please run next command `npm update caniuse-lite browserslist`
Started on port 8000
^C%

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.11 > master > cat logs.txt
5/2/2020, 1:50:08 PM: Connection received in root
5/2/2020, 1:50:09 PM: Connection received in root
```

### 1.12

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.10 > master ● > docker build -t frontend-example .
Sending build context to Docker daemon  910.3kB
...
Successfully built f90d592279d7
Successfully tagged frontend-example:latest

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.10 > master ● > docker run -d -p 5000:5000 frontend-example
73420155ca8ca416a9c14783f8a9338b01e6f19fda49c098536de91638d3a719

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.10 > master ● > cd ../1.11

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.11 > master ● > docker build -t backend-example .
...
Successfully built 302c2005d086
Successfully tagged backend-example:latest

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.11 > master ● > docker run -d -p 8000:8000 -v $(pwd)/logs.txt:/backend-example/logs.txt backend-example
62261118367bae3624ed60e5b6ead962e121e182cc8463ff09eaf3368056e6e1
```

### 1.13

```shell
ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.13 > master > docker build -t spring .
150f7b59ce24

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.13 > master > docker run -d -p 8080:8080 spring
07c7adddcb5750a2c947ffe9eee861193a3712b3d262a3eeefea5dabb591482a
```

### 1.14

```shell
 ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.14 > master > docker build -t rails .

Successfully built 8ed0f33bf13a
Successfully tagged rails:latest

ttalikka@apro13-5XHV2F > ~/devops_with_docker/1.14 > master ● > docker run -d -p 3000:3000 rails
57f56b20707b68dd63322aaac045106db0fc4b4daccf48261ea5555f40a02bb4
```
