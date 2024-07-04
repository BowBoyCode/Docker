# Docker Run Commands

- Run command in a new container from a tagged image:
``` bash
   docker run image:tag command
```
 - Run command in a new container in background and display its ID:
``` bash
   docker run --detach image command
```

 - Run command in a one-off container in interactive mode and pseudo-TTY:
``` bash
   docker run --rm --interactive --tty image command
```
 - Run command in a new container with passed environment variables:
   docker run --env 'variable=value' --env variable image command

 - Run command in a new container with bind mounted volumes:
   docker run --volume /path/to/host_path:/path/to/container_path image command

 - Run command in a new container with published ports:
   docker run --publish host_port:container_port image command

 - Run command in a new container overwriting the entrypoint of the image:
   docker run --entrypoint command image

 - Run command in a new container connecting it to a network:
   docker run --network network image

