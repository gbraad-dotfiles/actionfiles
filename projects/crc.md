# Compile CRC


### info

Definition to compile the [CRC](https://github.com/crc-org/crc) project.


### config
This action defines variables that will be used in all the actions

```ini
[compile]
    repo="https://github.com/crc-org/crc"
    repo_path="~/Projects/crc-org/crc"
    out_path="Projects/crc-org/crc/out"
    out_dest="${HOME}"
    flatten=0

[machine]
    name="crcbuild"
    from="golang"

[devenv]
    name="crcbuild"
    from="gofedora"
```

### vars
```sh
COMPILE_REPO_LOCAL=$(eval echo "${COMPILE_REPO_PATH}")
```

---

Local source interaction.

### exists-source
```sh
[ -d ${COMPILE_REPO_LOCAL} ]
```

### remove-source
```sh
rm -rf ${COMPILE_REPO_LOCAL}
```

### reset-source
```sh
cd ${COMPILE_REPO_LOCAL}
git reset --hard
cd -
```

### checkout-source
```sh
mkdir -p ${COMPILE_REPO_LOCAL}
git clone ${COMPILE_REPO} ${COMPILE_REPO_LOCAL}
```

### cd
This action changes to the local source directory.

```sh
if ! action ${FILENAME} source exists; then
  echo "Run: 'action ${FILENAME} source checkout' first."
  return
fi
cd ${COMPILE_REPO_LOCAL}
```

### code
```sh
if ! action ${FILENAME} source exists; then
  echo "Run: 'action ${FILENAME} source checkout' first."
  return
fi
code ${COMPILE_REPO_LOCAL}
```

---

These are actions to manage the `devenv` container that is used.

### remove-devenv
```sh
devenv ${DEVENV_NAME} remove
```

### start-devenv
```sh
devenv ${DEVENV_NAME} from ${DEVENV_FROM}
```

### stop-devenv
```sh
devenv ${DEVENV_NAME} stop
```

### exists-devenv
```sh
devenv ${DEVENV_NAME} exists
```

---

The compilation actions will be performed inside a `devenv`-container.

### make
```sh
devenv ${DEVENV_NAME} usercmd "cd ${COMPILE_REPO_PATH} && make"
```

### cross-make
```sh
devenv ${DEVENV_NAME} usercmd "cd ${COMPILE_REPO_PATH} && make cross"
```

### clean-make
```sh
devenv ${DEVENV_NAME} usercmd "cd ${COMPILE_REPO_PATH} && make clean"
```

### local-make
Temporary solution to run make locally on the host

```sh
cd ${COMPILE_REPO_PATH} && make
```

---

Default action is to compile. Performs the following:

  - checkout source if not exists
  - start `devenv` if not exists
  - `make clean`
  - `make cross`

### default alias compile
```sh
if ! action ${FILENAME} source exists; then
  action ${FILENAME} source checkout
fi
if ! action ${FILENAME} devenv exists; then
  action ${FILENAME} devenv start
fi
action ${FILENAME} make clean
action ${FILENAME} make cross
```
