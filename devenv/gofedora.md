# Fedora golang (container)

### config
```ini
[container]
   name="gofedora"
   from="gofedora"
```

### vars
```sh
CONTAINER_NAME="${FILENAME##*/}"
CONTAINER_NAME="${CONTAINER_NAME%.md}"
```

### ephemeral
```sh
devenv ${CONTAINER_NAME} env
```

### user
```sh
devenv ${CONTAINER_NAME} user
```

### root
```sh
devenv ${CONTAINER_NAME} root
```

### screen
```sh
devenv ${CONTAINER_NAME} screen
```

### remove
```sh
devenv ${CONTAINER_NAME} rm
```

### start
```sh
devenv ${CONTAINER_NAME} from ${CONTAINER_FROM}
```

### default status
```sh
devenv ${CONTAINER_NAME} status
```

### actions alias
```sh
action ${FILENAME} --list-actions | grep -vE '^(info|run|alias|vars|default|shared)$'
```
