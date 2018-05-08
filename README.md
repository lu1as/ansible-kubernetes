# ansible-kubernetes

ansible role collection to setup a kubernetes cluster

Compatible with:
- Fedora Atomic 27/28
- Raspbian 9

Hypervisor support for libvirt with KVM

## Setup

- create an inventory in `inventories/` based on the sample
- for virtual machines create a `cloud-config.yml` file in `vars/`

## Create virtual machines

    ansible-playbook -i inventories/<env> vm-creation.yml

## Install kubernetes

    ansible-playbook -i inventories/<env> kubernetes.yml

### Fix firewall after reboot (Fedora Atomic)

    ansible-playbook -i inventories/<env> kubernetes.yml --tags firewall

## Configure kubectl client

    ansible-playbook -i inventories/<env> client.yml
    kubectl config use-context <kube-context>