# docker_base
docker base images for dev

- [python 3.12 base image](https://hub.docker.com/repository/docker/zeroact/zpython/general)
- [ai dev](https://hub.docker.com/repository/docker/zeroact/ai_dev/general)

## Release
- 24.10.31
  - ipython
  - pytorch
  - tools for [unstructured](https://github.com/Unstructured-IO/unstructured)(poputil, tessoract, etc...)
  - usage
    ```shell
    docker pull zeroact/ai_dev:3.12
    docker run -it -p 2222:22 -d --name ai_dev zeroact/ai_dev:3.12 /usr/sbin/sshd -D
    ssh -p 2222 root@localhost
    # root
    ```

## It has installed
- basic build tools
- git
- simple monitoring tools
- nanum font
- python3.x
- ssh server
- etc ..


## RUN
```bash
docker pull zeroact/zpython:3.12
docker run \
    -itd \
    --rm \
    --name dev \
    -v $(pwd):/ws \
    -p 2222:22 \
    --gpus all \
    zeroact/zpython:3.12

# docker exec -it dev /bin/bash
# or
ssh -p 2222 root@localhost
# root password is 'root'
```


## Build Images
```bash
docker build --no-cache -t zeroact/zpython:3.12 -f Dockerfile.python312 .
```


## Cheat Sheet

### remove container
```bash
docker rm -f dev
```

### logs
```bash
docker logs -f dev
```

### known_hosts issue
```bash
rm /home/root/.ssh/known_hosts
```
