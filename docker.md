# Docker

## Often used commands

```bash
$ docker version
$ docker ps
$ docker container ls
$ docker inspect CONTAINER|IMAGE
$ docker images --all
$ docker run -p HOSTPORT:CONTAINERPORT -v HOSTDIR:~CONTAINERDIR IMAGE
$ docker logs CONTAINER
$ docker stop CONTAINER
$ docker start CONTAINER
$ docker exec -it CONTAINER bash
$ docker rm CONTAINER
$ docker volume ls
$ docker volume inspect VOLUME
$ docker system df
```

## Releasing space

By default `docker system prune` won't touch volumes or images (other than dangling). If you're sure you can pull/rebuild all needed images (as should be the case, but sometimes the world is not perfect), you can run

```bash
$ docker system prune --all
```

The previous command doesn't touch volumes. If you're on a development machine where you can rebuilt all the data in volumes, you can run this command (but notice that all databases you run as containers **will be deleted**):

```bash
$ docker system prune --all --volumes
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
