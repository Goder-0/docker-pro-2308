## cli example

### 1. [Download an image from a registry](https://docs.docker.com/engine/reference/commandline/pull/)
- 사용법
```shell
 docker pull [OPTIONS] NAME[:TAG|@DIGEST]
```
- 예제
```shell
docker pull httpd
```

### 2. [List images](https://docs.docker.com/engine/reference/commandline/images/)
- 사용법
```shell
 docker images [OPTIONS] [REPOSITORY[:TAG]]
```
- 예제
```shell
 docker images
```

### 3. [Create and run a new container from an image](https://docs.docker.com/engine/reference/commandline/run/)
- 사용법
```shell
 docker run [OPTIONS] IMAGE [COMMAND] [ARG...]
```
- 예제
```shell
 docker run httpd
 docker run --name secondContainer httpd
 docker run -p 8888:80 -v /Users/jk/wanted/2308/docker-pro-2308/lecture/1st:/usr/local/apache2/htdocs httpd
```

### 4. [Start one or more stopped containers](https://docs.docker.com/engine/reference/commandline/start/)
- 사용법
```shell
 docker start [OPTIONS] CONTAINER [CONTAINER...]
```
- 예제
```shell
 docker start c8274d6a6273
```

### 5. [Stop one or more running containers](https://docs.docker.com/engine/reference/commandline/stop/)
- 사용법
```shell
 docker stop [OPTIONS] CONTAINER [CONTAINER...]
```
- 예제
```shell
 docker stop 9b0f49de746c
 docker stop -a
```

### 6. [Fetch the logs of a container](https://docs.docker.com/engine/reference/commandline/logs/)
- 사용법
```shell
 docker logs [OPTIONS] CONTAINER
```
- 예제
```shell
docker logs second
docker logs second -f
```

### 7. [Remove one or more containers](https://docs.docker.com/engine/reference/commandline/rm/)
- 사용법
```shell
 docker rm [OPTIONS] CONTAINER [CONTAINER...]
```
- 예제
```shell
docker rm 6026ab9b44cc
docker rm second -f
```

### 8. [Remove one or more images](https://docs.docker.com/engine/reference/commandline/rmi/)
- 사용법
```shell
 docker rmi [OPTIONS] IMAGE [IMAGE...]
```
- 예제
```shell
docker rmi 6026ab9b44cc
```

### 9. [Execute a command in a running container](https://docs.docker.com/engine/reference/commandline/exec/)
- 사용법
```shell
 docker exec [OPTIONS] CONTAINER COMMAND [ARG...]
```
- 예제
```shell
docker exec -it awesome_elion /bin/sh
```

### 10. [Manage containers](https://docs.docker.com/engine/reference/commandline/container/)
- 사용법
```shell
 docker container COMMAND
```

#### 10-1. [Remove all stopped containers](https://docs.docker.com/engine/reference/commandline/container_prune/)
- 사용법
```shell
 docker container prune [OPTIONS]
```
- 예제
```shell
 docker container prune
```

#### 10-2. [Display a live stream of container(s) resource usage statistics](https://docs.docker.com/engine/reference/commandline/container_stats/)
- 사용법
```shell
 docker container stats [OPTIONS] [CONTAINER...]
```
- 예제
```shell
 docker container stats
```

### 11. [Manage images](https://docs.docker.com/engine/reference/commandline/image/)
- 사용법
```shell
 docker image COMMAND
```

#### 11-1. [Remove unused images](https://docs.docker.com/engine/reference/commandline/image_prune/)
- 사용법
```shell
 docker image prune [OPTIONS]
```
- 예제
```shell
 docker image prune
```

#### 11-2. [Display detailed information on one or more images](https://docs.docker.com/engine/reference/commandline/image_inspect/)
- 사용법
```shell
 docker image inspect [OPTIONS]
```
- 예제
```shell
docker image inspect httpd
```

#### 11-3. [Create a tag TARGET_IMAGE that refers to SOURCE_IMAGE](https://docs.docker.com/engine/reference/commandline/image_tag/)
- 사용법
```shell
 docker image tag SOURCE_IMAGE[:TAG] TARGET_IMAGE[:TAG]
```
- 예제
```shell
docker image tag my-httpd drumgrammer/my-httpd:latest
```

### 12. [Upload an image to a registry](https://docs.docker.com/engine/reference/commandline/push/)
- 사용법
```shell
 docker push [OPTIONS] NAME[:TAG]
```
- 예제
```shell
docker push drumgrammer/my-httpd:latest
```

### 13. [Log in to a registry](https://docs.docker.com/engine/reference/commandline/login/)
- 사용법
```shell
 docker login [OPTIONS] [SERVER]
```
- 예제
```shell
 docker login
```

### 14. [Log out from a registry](https://docs.docker.com/engine/reference/commandline/logout/)
- 사용법
```shell
 docker logout [SERVER]
```
- 예제
```shell
 docker logout
```

## Dockerfile 활용
1. Dockerfile 예제
```Dockerfile
FROM httpd:latest
COPY  index.html /usr/local/apache2/htdocs/index.html
EXPOSE 80
```
2. 이미지 만들기
```shell
docker build -t my-httpd .
```
3. 도커파일로 생성된 이미지로 컨테이너 실행하기
```shell
docker run -d -p 8888:80 my-httpd
```
