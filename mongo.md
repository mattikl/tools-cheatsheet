# MongoDB


    mongo mongodb://user:password@127.0.0.1:27017/dbname

[Mongo shell docs](https://docs.mongodb.com/manual/mongo/)

## Common shell operations

```
db.foo.find()
db.foo.find({bar: "baz"})
db.foo.find({bar: { $regex: /^baz/} })
db.foo.find({bar: "baz"}, {"quux.name": 1})
db.foo.count({bar: "baz"})
db.foo.insert({bar: "baz"})
db.foo.update({bar: "baz"}, {$set: {quux: "foo"}})
```

## Getting info about db

```
show dbs
db.hostInfo()
db.stats()
db.getCollectionNames()
db.printCollectionStats()
```

## Brew, Docker

To install the command line tools on Mac (as of 2020-07-07):

```sh
$ brew tap mongodb/brew
$ brew install mongodb-community
```

### Running with Docker

Run in localhost port 12345:

### For quick testing

```sh
$ docker run -d --rm -p 12345:27017 --name mongo-test mongo
```

The (mongo image)[https://hub.docker.com/_/mongo] creates two anonymous volumes (config and data). When run with the `--rm` option, stopping the container removes the container as well as these volumes.

### When you need to persist data

```sh
$ docker run -d -p 12345:27017 --name mongo-test mongo
```

You need to remove the `mongo-test` container to use the same name again. You also need to remove the volumes by yourself.

### Working with the container

Run mongo shell inside container:

```sh
$ docker exec -it mongo-test mongo
```

View logs:

```sh
$ docker logs mongo-test
```

Stop container:

```sh
$ docker stop mongo-test
```

If ran without the `--rm` flag, you can start it again with

```sh
$ docker start mongo-test
```

## GUIs

[Robo 3T](https://robomongo.org/)

## Dumping and restoring
