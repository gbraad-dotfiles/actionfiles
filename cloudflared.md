# Cloudflare (container)

### info

  - https://github.com/spotsnel/cloudflared-systemd/


### config
```ini
[container]
  image="ghcr.io/spotsnel/cloudflared-systemd/fedora:latest"
  name="flaresys"
  args="--network=host"
  shell="bash"
```

### run
```sh
podman run -d --name=${CONTAINER_NAME} \
    --hostname $HOSTNAME-${CONTAINER_NAME} \
    --systemd=always \
    ${CONTAINER_ARGS[@]} \
    ${CONTAINER_IMAGE}
```

### shell
```sh evaluate
podman exec -it ${CONTAINER_NAME} ${CONTAINER_SHELL}
```
