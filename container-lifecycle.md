# Container Lifecycle

The "main process" refers to the initial command that is executed when you run a container. This process is what keeps the container running. When the main process terminates, the container stops.

In a Docker Ubuntu container, the main process is typically a shell or a service manager like systemd, depending on how the image was configured. For example, if you start a Ubuntu container with the command docker run -it ubuntu, the default behavior is to run an interactive shell (bash) as the main process.

## Ubuntu Cotainer

If we want to create an Ubuntu container and keep it running we can use the follow command:

```sh
docker run --name alwaysup -d ubuntu tail -f /dev/null
```

Where:

- **`-d`:** This flag stands for "detached mode." It tells Docker to run the container in the background (in the background, not attached to your terminal).
- **`-d`:**  This is the command that will be executed as the main process inside the container. It's a bit of a workaround. `tail -f /dev/null` essentially tells the container to do nothing and keep running indefinitely. The `tail` command is used to display the end of a file, and `/dev/null` is a special file that discards everything written to it. So, effectively, this command keeps the container running without doing any actual work.

### Interactive mode

Once the container is created and running whe can enter to the interactive mode by executing the `-it` flag followed by the _container name_ and the `bash` command.

```sh
docker exec -it alwaysup bash
```

### Stopping the container

When working with different Operating Systems, the command may vary a little.

- **UNIX like systems:**

If you're using Linux you can kill it by exiting the container and executing the follow command to know the _process Id_.

```sh
docker inspect --format '{{.State.Pid}}' alwaysup
```

Knowing the _process ID_ is just matter to executing the `kill` command followed by the _process ID_.

```sh
kill processID
```

- **Windows:**

To stop the container in Windows we can use the command.

```sh
docker stop containerName
```
