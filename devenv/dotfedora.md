# Fedora dotfiles (container)

### config
```ini
[container]
   name="dotfedora"
   from="dotfedora"
```

### vars
```sh
if [ -z "${CONTAINER_NAME}" ]; then
  CONTAINER_NAME="${FILENAME##*/}"
  CONTAINER_NAME="${CONTAINER_NAME%.md}"
fi
```

### ephemeral
```sh evaluate
devenv ${CONTAINER_NAME} env
```

### user
```sh evaluate
devenv ${CONTAINER_NAME} user
```

### root
```sh evaluate
devenv ${CONTAINER_NAME} root
```

### screen
```sh evaluate
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

### alias actions
```sh
action ${FILENAME} --list-actions | grep -vE '^(info|run|alias|vars|default|shared)$'
```
