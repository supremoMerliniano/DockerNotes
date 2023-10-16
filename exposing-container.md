# Exposing a Docker Container

You can expose a docker container by declaring the external and internal ports where we can connect to it. When creating the Docker container by using the `run` command, whe can specify the ports in the parameters of the `-p` (_publish_) _flag_. The command structure is the follow:

```sh
docker run -d --name containerName -p externalPort:internalPort dockerImage 
```

**Example:**

```sh
docker run -d --name proxy -p 8080:80 nginx
```

## Showing Logs

When working with dettached terminal containers we can see the logs by typing in other terminal the follow command.

```sh
docker logs -f containerName
```
