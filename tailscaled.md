# Tailscale (container)

### info

  - https://github.com/spotsnel/tailscale-systemd

### config
```ini
[container]
  image="ghcr.io/spotsnel/tailscale-systemd/fedora:latest"
  name="scalesys"
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

### login
```sh evaluate
podman exec ${CONTAINER_NAME} tailscale up -qr
```

### shell
```sh evaluate
podman exec -it ${CONTAINER_NAME} ${CONTAINER_SHELL}
```

