# inkscope-ansible

tested ok on ubuntu 16.04 and centos7

## Purpose

This playbook intends to replace the  installation of Inkscope from packages (deb, rpm). Inkscope packages are no more maintained.

This will install Inkscope and all its dependencies directly from the Github repository.


## Pre-requisites

Ceph must be installed on the targeted server, with the convenient ceph configuration file and admin keyring.

**Take also care of:**

-   system date and time : install ntp if necessary

-   firewall : manage rules or disable it 

-   selinux : works fine when disabling it


## Installation from github

You can install directly from the source on github by cloning the repository :

    git clone https://github.com/inkscope/inkscope-ansible.git

Install ansible used roles by the command:

    ansible-galaxy install -r requirements.yaml


## Configuration and usage

This project assumes you have a basic knowledge of how ansible works and have already prepared your hosts for configuration by ansible.

### Inventory

The ansible inventory file defines the host where you want to install Inkscope. The default location for an inventory file is /etc/ansible/hosts but this file can be placed anywhere and used with the -i flag of ansible-playbook.
An example inventory file would look like:

    [inkscope]
    my_server

### inkscope-ansible configuration

The configuration for your inkscope installation will be set by the use of ansible variables.
All of these options and their default values are defined in the **vars/my_inkscope.yaml** file at the root of the inkscope-ansible project.
**Apache is installed by the playbook; it works fine when using 8080 as port for inkscope vhost**

### Playbook

Inkscope installation with the playbook could be run by the command:

    ansible-playbook inkscope.yaml
