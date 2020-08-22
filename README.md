![grants_badge](./grants_badge.png)

# Subscan Essentials

![License: GPL](https://img.shields.io/badge/license-GPL-blue.svg)
[![Go Report Card](https://goreportcard.com/badge/github.com/itering/subscan)](https://goreportcard.com/report/github.com/itering/subscan)
![subscan](https://github.com/itering/subscan/workflows/subscan/badge.svg)

Subscan Essentials is a high-precision blockchain explorer scaffold project. 
It supports substrate-based blockchain networks with developer-friendly interface, standard or custom module parsing capabilities. 
It's developed by the Subscan team and used in subscan.io. 
Developers are free to use the codebase to extend functionalities and develop unique user experiences for their audiences.

## Contents

- [Feature](#Feature)
- [QuickStart](#QuickStart)
  - [Requirement](#Requirement)
  - [Structure](docs/tree.md)
  - [Installation](#Install)
  - [UI](#UI)
  - [Usage](#Usage)
  - [Docker](#Docker)
  - [Test](#Test)
- [Contributions](#Contributions)
- [LICENSE](#LICENSE)
- [Resource](#Resource)

## Feature

1. Support Substrate network [custom](/custom_type.md) type registration 
2. Support index Block, Extrinsic, Event, log
3. More data can be indexed by custom [plugins](/plugins)
4. [Gen](https://github.com/itering/subscan-plugin/tree/master/tools) tool can automatically generate plugin templates
5. Built-in default HTTP API [DOC](/docs/index.md)


## QuickStart

### Requirement

* Linux / Mac OSX
* Git
* Golang 1.12.4+
* Redis 3.0.4+
* MySQL 5.6+
* Node 8.9.0+

### Install

```bash
./build.sh install

//UI
cd ui && yarn && yarn dev
```

### UI

The ui part is built with [nuxt.js](https://nuxtjs.org/) and [amis](https://github.com/baidu/amis)

Demo: [blocks](/ui/plugins/blocks.js), refer to [amis docs](https://baidu.gitee.io/amis/docs/index) for further detail.

Please change proxy target in nuxt.config.js to your server name in development.

```js
proxy: {
   "/api": {
      target: "https://your_server_name.com",
      secure: false,
      changeOrigin: true,
      pathRewrite: {
         "^/api": "/api"
      }
   },
}
```

### Usage

- Run

```bash
1.subscan --conf configs //rpc service
2.subscan start substrate //sync block data to mysql
  sync config = util/env.go

```

- Help 

```
NAME:
   SubScan - SubScan Backend Service, use -h get help

USAGE:
   main [global options] command [command options] [arguments...]

VERSION:
   1.0

DESCRIPTION:
   SubScan Backend Service, substrate blockchain explorer

COMMANDS:
     start    Start one worker, E.g substrate
     stop     Stop one worker, E.g substrate
     install  Create database and create default conf file
     help, h  Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --conf value   (default: "../configs")
   --help, -h     show help
   --version, -v  print the version


```

### Docker

Run mysql and redis container

```bash
docker-compose -f docker-compose.db.yml up  -d
```

Run subscan service

```bash
docker-compose build
docker-compose up -d
```

### Test

```bash
go test ../.
```


## Contributions

We welcome contributions of any kind. Issues labeled can be good (first) contributions.

## LICENSE

GPL-3.0


## Resource
 
- [ITERING] https://github.com/itering
- [Darwinia] https://github.com/darwinia-network/darwinia
