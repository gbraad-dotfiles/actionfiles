# Fedora dotfiles (virual machine)


### config
```ini
[machine]
  name="dotfedora"
  from="dotfedora"
```

### vars
```sh
MACHINE_NAME="${FILENAME##*/}"
MACHINE_NAME="${CONTAINER_NAME%.md}"
```

### download
```sh
machine ${MACHINE_FROM} download
```

### create
```sh
machine ${MACHINE_NAME} from ${MACHINE_FROM}
```

### exists
```sh
machine ${MACHINE_NAME} exists
```

### start
```sh
machine ${MACHINE_NAME} start
```

### stop
```sh
machine ${MACHINE_NAME} stop
```

### remove
```sh
machine ${MACHINE_NAME} rm
```

### default status
```sh
machine ${MACHINE_NAME} status
```

### ssh
```sh evaluate
machine ${MACHINE_NAME} ssh
```

### alias actions
```sh
action ${FILENAME} --list-actions | grep -vE '^(info|run|alias|vars|default|shared)$'
```

