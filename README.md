# govm - A CLI for launching in-Container VMs (Virtual Machines)

NOTICE
------
This project is on intensive development. If you have issues when trying to use it, please let us know, we don't want to make you cry.

Introduction
------------
``govm`` is a Docker-based tool that will launch your pet VM inside docker containers. It will use Docker networking layer and will map it to your VM.

Key Features
------------
- Uses Docker networking
- Cloud Init support
- Copy-on-write images
- EFI support
- Cloud-Init and RAW images support

Requirements
---------------
- Go 1.7+
- Docker

Get the project
---------------
```
go get -u github.intel.com/clrgdc/govm/...
```


Launch your first VM (Ubuntu 16.04 cloud image)
-----------------------------------------------
```
# Download Ubuntu 16.04 cloud image
curl -Ok https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-disk1.img
# Launch your VM
govm create --image xenial-server-cloudimg-amd64-disk1.img --cloud
```

**Output**
```
no vnc
[hopeful_euler]
IP Address: 172.17.0.4
```

# Log into your vm
```
ssh ubuntu@172.17.0.4
```

``govm`` help
-------------

```
NAME:
   govm - Virtual Machines on top of Docker containers

USAGE:
   govm [global options] command [command options] [arguments...]

VERSION:
   0.0.0

COMMANDS:
     create, c      Create a new govm
     delete, d      Delete govms
     list, ls       List govms
     compose, co    Deploy Govms from yaml templates
     connect, conn  Get a shell from a Govm
     help, h        Shows a list of commands or help for one command

GLOBAL OPTIONS:
   --workdir value  Alternate working directory. Default: ~/govm
   --help, -h       show help
   --version, -v    print the version
```

More cloud init stuff?
----------------------

If you want to boot cloud images, edit the template files under $HOME/govm/cloud-init/openstack/latest/ to fit your own needs and use the `-cloud` flag.
For more information, please see the cloud-init documentation: https://cloudinit.readthedocs.io/en/latest/

based on https://github.com/BBVA/kvm

Questions, issues or suggestions
--------------------------------

http://github.intel.com/clrgdc/govm/issues