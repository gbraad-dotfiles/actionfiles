# Fedora dotfiles (virual machine)

## 

### info

### vars
```sh
MACHINENAME="dotfedora"
```

---

### download
```sh
machine ${MACHINENAME} download
```

### create
```sh
machine ${MACHINENAME} create
```

### exists
```sh
machine ${MACHINENAME} exists
```

### start
```sh
machine ${MACHINENAME} start
```

### stop
```sh
machine ${MACHINENAME} stop
```

### rm remove
```sh
machine ${MACHINENAME} rm
```

### status
```sh
machine ${MACHINENAME} status
```

### default alias
```sh
action ${FILENAME} --list-actions
```

### console ssh
```sh evaluate
machine ${MACHINENAME} ssh
```
