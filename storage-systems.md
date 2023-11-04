# Storage Systems

When working with Docker we can encounter with several storage systems.

## Bind Mount

A bind mount in Docker is a way to mount a directory or file from the host machine into a container. This allows the container to access the data on the host machine as if it were its own.

To create a bind mount, you use the `-v` option when running the docker run command. The `-v` option takes **two arguments**: the **path** to the directory or **file** on the **host machine**, and the **path** to the directory or **file** in the **container**.

**For example**, the following command would mount the `/data` directory on the host machine into the `/opt/data` directory in the container:

```sh
docker run -it -v /data:/opt/data my-container
```

Here is an **example** of how to use a bind mount to **mount** a source code directory from the **host machine** into a **container**:

```sh
docker run -it -v $(pwd):/src my-container
```

This command would mount the current working directory on the host machine into the `/src` directory in the container. Once the container is running, you can access the source code in the `/src` directory in the container as if it were stored on the host machine.
