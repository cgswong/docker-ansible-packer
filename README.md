docker-ansible-packer
=====================

packer setup for creating docker images using ansible

This project is used to build the image provided at: https://index.docker.io/u/egghead/ubuntu-ansible-1.4/

If you have `packer` & `docker` installed, you can use this project to [build](https://github.com/eggsby/docker-ansible-packer/blob/master/build.json) a base image to automate creation of docker images using ansible.

    packer build build.json
    # builds ubuntu-ansible-1.4 base image

To use the new base image check out the [usage.json](https://github.com/eggsby/docker-ansible-packer/blob/master/usage.json) file

    packer build usage.json
    # builds a new image using ansible & the ubuntu-ansible-1.4 image
