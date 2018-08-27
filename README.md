# ansible-kubernetes

ansible role collection to setup a kubernetes cluster

Compatible with:
- Fedora Atomic 28
- Raspbian 9
- Debian 9 (Stretch)

Hypervisor support for libvirt with KVM

## Setup

- create an inventory in `inventories/` based on the sample
- for virtual machines create a `cloud-config.yml` file in `vars/`

## Create virtual machines

    ansible-playbook -i inventories/<env> vm-creation.yml

## Install kubernetes

    ansible-playbook -i inventories/<env> kubernetes.yml

## Configure kubectl client

    ansible-playbook -i inventories/<env> client.yml
    kubectl config use-context <kube-context>