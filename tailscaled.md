# Tailscale (container)

### info

  - https://github.com/spotsnel/tailscale-systemd

### config
```ini
[container]
  name="scalesys"
```

### run
```sh 
podman run -d --name=${CONTAINER_NAME} \
    --hostname $HOSTNAME-scalesys --network=host --systemd=always \
    ghcr.io/spotsnel/tailscale-systemd/fedora:latest
```

### login
```sh evaluate
podman exec ${CONTAINER_NAME} tailscale up -qr
```

### shell
```sh evaluate
podman exec -it ${CONTAINER_NAME} zsh
```

