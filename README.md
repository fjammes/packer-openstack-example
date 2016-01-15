# packer-openstack-example
Produce an openstack image using packer

# Pre-requisite
Install packer: https://www.packer.io/intro/getting-started/setup.html
Here we use packer 0.8.6.

# Convert to QCOW2

I was able to make a snapshot (raw) , and then download, convert, and upload again with client commands like :
% nova image-list
     (find image/snapshot id)
% glance image-download  --file my.test.raw  ba2fb964-1a2e-4dc0-a756-7d1e53d0c209
% qemu-img convert -O qcow2 my.test.raw my.test.qcow
% glance image-create --name daues-qcow2-test  --disk-format qcow2  --file ./my.test.qcow  --container-format bare
