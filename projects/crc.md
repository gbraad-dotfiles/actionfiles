# Compile CRC


### info

Definition to compile the [CRC](https://github.com/crc-org/crc) project.


### vars
This action defines variables that will be used in all the actions

```sh
PROJHOME="~/Projects"
CRCSOURCE="${PROJHOME}/crc-org/crc"
CRCLOCAL=$(eval echo "${CRCSOURCE}")
CRCDEVENV="gofedora"
```

### shared

---

Local source interaction.

### exists-source
```sh
[ -d ${CRCLOCAL} ]
```

### remove-source
```sh
rm -rf ${CRCLOCAL}
```

### reset-source
```sh
cd ${CRCLOCAL}
git reset --hard
cd -
```

### checkout-source
```sh
mkdir -p ${CRCLOCAL}
git clone https://github.com/crc-org/crc ${CRCLOCAL}
```

### cd
This action changes to the local source directory.

```sh
if ! action ${FILENAME} source exists; then
  echo "Run: 'action ${FILENAME} source checkout' first."
  return
fi
cd ${CRCLOCAL}
```

### code
```sh
if ! action ${FILENAME} source exists; then
  echo "Run: 'action ${FILENAME} source checkout' first."
  return
fi
code ${CRCLOCAL}
```

---

These are actions to manage the `devenv` container that is used.

### remove-devenv
```sh
devenv ${CRCDEVENV} remove
```

### start-devenv
```sh
devenv ${CRCDEVENV} noinit
```

### stop-devenv
```sh
devenv ${CRCDEVENV} stop
```

### exists-devenv
```sh
devenv ${CRCDEVENV} exists
```

---

The compilation actions will be performed inside a `devenv`-container.

### make
```sh
devenv ${CRCDEVENV} usercmd "cd ${CRCSOURCE} && make"
```

### cross-make
```sh
devenv ${CRCDEVENV} usercmd "cd ${CRCSOURCE} && make cross"
```

### clean-make
```sh
devenv ${CRCDEVENV} usercmd "cd ${CRCSOURCE} && make clean"
```

### local-make
Temporary solution to run make locally on the host

```sh
cd ${CRCLOCAL} && make
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
