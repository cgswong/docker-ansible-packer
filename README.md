docker-ansible-packer
=====================

packer setup for creating docker images using ansible

This project is used to build the image provided at: https://index.docker.io/u/egghead/ubuntu-ansible-1.4/

If you have `packer` & `docker` installed, you can use this project to [build](https://github.com/eggsby/docker-ansible-packer/blob/master/build.json) a base image to automate creation of docker images using ansible.

    packer build build.json
    # builds ubuntu-ansible-1.4 base image

To use the new base image check out the [usage.json](https://github.com/eggsby/docker-ansible-packer/blob/master/usage.json) file

    packer build usage.json
    ==> docker: Creating a temporary directory for sharing data...
    ==> docker: Pulling Docker image: egghead/ubuntu-ansible-1.4
        docker: Pulling repository egghead/ubuntu-ansible-1.4
        docker: c4b6ccea1241: Download complete
        docker: c4b6ccea1241: Download complete
    ==> docker: Starting docker container with /bin/bash
        docker: Container ID: aa2db1214e4134ef556aa5b795542aec74cd1cf6e759a45bc6b063aac9307501[0m
    ==> docker: Provisioning with Ansible...
        docker: Creating Ansible staging directory...
        docker: Creating directory: /tmp/packer-provisioner-ansible-local
        docker: Uploading main Playbook file...
        docker: Executing Ansible: ansible-playbook /tmp/packer-provisioner-ansible-local/provision.yaml -c local -i "127.0.0.1,"
        docker:
        docker: PLAY [all] ********************************************************************
        docker:
        docker: GATHERING FACTS ***************************************************************
        docker: ok: [127.0.0.1]
        docker:
        docker: TASK: [debug msg="Hello, docker!"] ********************************************
        docker: ok: [127.0.0.1] => {
        docker: "msg": "Hello, docker!"
        docker: }
        docker:
        docker: TASK: [shell whoami] **********************************************************
        docker: changed: [127.0.0.1]
        docker:
        docker: PLAY RECAP ********************************************************************
        docker: 127.0.0.1                  : ok=3    changed=1    unreachable=0    failed=0
        docker:
    ==> docker: Exporting the container
    ==> docker: Killing the container: aa2db1214e4134ef556aa5b795542aec74cd1cf6e759a45bc6b063aac9307501
    Build 'docker' finished.

    ==> Builds finished. The artifacts of successful builds are:
    --> docker: Exported Docker file: ansible-provisioned.tar
