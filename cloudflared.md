# Cloudflare (container)

### info

  - https://github.com/spotsnel/cloudflared-systemd/


### run
```sh
podman run -d --name=flaresys \
    --hostname $HOSTNAME-flaresys --network=host --systemd=always \
    ghcr.io/spotsnel/cloudflared-systemd/fedora:latest
```
