# Docker

## Often used commands

```bash
$ docker version
$ docker ps
$ docker container ls
$ docker inspect CONTAINER
$ docker images --all
$ docker run -p HOSTPORT:CONTAINERPORT -v HOSTDIR:~CONTAINERDIR IMAGE
$ docker logs CONTAINER
$ docker stop CONTAINER
$ docker start CONTAINER
$ docker exec -it CONTAINER bash
$ docker rm CONTAINER
$ docker volume ls
$ docker volume inspect VOLUME
```

## Saving and loading images

```bash
$ docker save foobar:latest | gzip > foobar.tar.gz
$ docker load < foobar.tar.gz
```

## Copying files from container

```bash
$ docker cp CONTAINER:/path/to/file_or_dir/ dest_folder
```

Other approaches: mounting a volume, `docker export` to export container’s filesystem as a tar archive.
