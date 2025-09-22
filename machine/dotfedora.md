# Fedora dotfiles (virual machine)

## 

### info

### vars
```sh
MACHINENAME="dotfedora"
SVCNAME=dotfiles-machine-${MACHINENAME}
```

---

### install-service
```sh
machine-export-service ${MACHINENAME}
```

### enable-service
```sh
systemctl --user enable --now ${SVCNAME}
```

### disable-service
```sh
systemctl --user disable --now ${SVCNAME}
```

### restart-service
```sh
action ${FILENAME} service stop
action ${FILENAME} service start
```

### start-service
```sh
systemctl --user start ${SVCNAME}
```

### stop-service
```sh
systemctl --user stop ${SVCNAME}
```

### status-service
```sh
systemctl --user status ${SVCNAME}
```

### active-service
```sh
systemctl --user is-active ${SVCNAME}
```

### journal-service
```sh
journalctl --user -u ${SVCNAME} -f
```

### run-service
```sh
machine ${MACHINENAME} service
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
