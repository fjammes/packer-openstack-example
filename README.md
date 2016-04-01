# packer-openstack-example
Produce an openstack image using packer

# Pre-requisite
Install packer: https://www.packer.io/intro/getting-started/setup.html.
In this example, we use packer 0.8.6.

# Build image

```
# Template for NCSA Openstack platform
% packer build packer_template.ncsa.json
```

# Convert to QCOW2

## Install nova api:

See http://docs.openstack.org/user-guide/common/cli_install_openstack_command_line_clients.html

### example for debian-like systems
```
% sudo apt-get install python-novaclient python-glanceclient
```

## Install qemu-img

## Download, convert, and upload again

Use client commands like :
```
% nova image-show docker-zeroconf-image
     (find image/snapshot id)
% cd <20GB+PARTITION>
% glance image-download --file img.raw <IMAGE-ID>
% qemu-img convert -O qcow2 img.raw img.qcow
% glance image-create --name ubuntu-15.04-qserv  --disk-format qcow2  --file ./img.qcow  --container-format bare
```
