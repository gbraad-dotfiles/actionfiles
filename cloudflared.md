# Cloudflare (container)

### info

  - https://github.com/spotsnel/cloudflared-systemd/


### config
```ini
[container]
  name="flaresys"
```

### run
```sh
podman run -d --name=${CONTAINER_NAME} \
    --hostname $HOSTNAME-flaresys --network=host --systemd=always \
    ghcr.io/spotsnel/cloudflared-systemd/fedora:latest
```

### shell
```sh evaluate
podman exec -it ${CONTAINER_NAME} zsh
```
