# packer-openstack-example
Produce an openstack image using packer

# Pre-requisite
Install packer: https://www.packer.io/intro/getting-started/setup.html
Here we use packer 0.8.6.

# Build image

% packer build packer_template.json

# Convert to QCOW2

Install nova api:
http://docs.openstack.org/user-guide/common/cli_install_openstack_command_line_clients.html

# example for debian-like systems
% sudo apt-get install python-novaclient python-glanceclient

Download, convert, and upload again with client commands like :
% nova image-show docker-zeroconf-image
     (find image/snapshot id)
% cd <20GB+PARTITION>
% glance image-download --file ubuntu-qserv.raw <IMAGE-ID>
% qemu-img convert -O qcow2 ubuntu-qserv.raw ubuntu-qserv.qcow
% glance image-create --name ubuntu-qserv  --disk-format qcow2  --file ./ubuntu-qserv.qcow  --container-format bare
