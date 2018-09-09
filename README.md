# Setup

## Raspberry Pi

### Raspbian
- Go to https://www.raspberrypi.org/downloads/raspbian/ and download the raspbian image either with or without desktop.

- Go to https://etcher.io/ and download the etcher tool.

- Insert the micro SD card to the PC and intall the downloaded image via etcher.

### Boot Raspberry Pi

- Insert the MicroSD memory card into the Raspberry Pi
- Connect the USB keyboard
- Connect the HDMI cable
- Connect the Ethernet cable
- Connect the Power cable to boot the raspberry pi

### Setup SSH

- logon via user (pi) and pwd (raspberry)
- go to the raspberry config via
```bash
pi@raspberrypi:~ $ sudo raspi-config
```
- change user password via menu
- go to interface setting and enable SSH
- get and remember the ip address via
```bash
pi@raspberrypi:~ $ sudo ifconfig
```
- reboot the pi with
```bash
pi@raspberrypi:~ $ sudo reboot now
```

- switch to your "normal" pc
- get putty from https://www.putty.org/
- run putty and connect via ip address and port 22 connection type SSH
- you should now be connected to the pi via SSH

see also: https://www.w3schools.com/nodejs/nodejs_raspberrypi.asp


### Node.js Setup

- update & upgrade
```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```
- get nodejs
```
$ curl -sL https://deb.nodesource.com/setup_10.x | sudo -E bash -
$ sudo apt-get install -y nodejs
```
- install typescript
```
$ sudo npm install -g typescript
```

## Local development

### Setup

- create a project folder (PiBox) and init a project via:
```
$ npm init
```
- adapt the package json with the start script:
```json
"start": "tsc && node dist/index.js"
```

- add the typescript config file
```json
{
  "compilerOptions": {
    "module": "commonjs",
    "declaration": false,
    "noImplicitAny": false,
    "removeComments": true,
    "noLib": false,
    "allowSyntheticDefaultImports": true,
    "emitDecoratorMetadata": true,
    "experimentalDecorators": true,
    "target": "es6",
    "sourceMap": true,
    "allowJs": true,
    "outDir": "./dist",
    "baseUrl": "./src"
  },
  "include": [
    "src/**/*"
  ],
  "exclude": [
    "node_modules",
    "**/*.spec.ts"
  ]
}
```
- install GPIO module for the pi (onoff)
```
$ npm install onoff -save
```

- create a folder src
- create a file index.ts in src
