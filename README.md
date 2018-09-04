# ansible-kubernetes

ansible role collection to setup a kubernetes cluster

Compatible with:
- Fedora Atomic 28
- Raspbian 9
- Debian 9 (Stretch)

Hypervisor support for Debian (libvirt with KVM)

## Setup

- create an inventory in `inventories/` based on the sample
- for virtual machines create a `cloud-config.yml` file in `vars/`
- IMPORTANT: Inventory hostnames will be used as hostnames. For example inventory hostname `master1` and kube_domain `kube.example.com` would result to `master1.kube.example.com`

## Create virtual machines

    ansible-playbook -i inventories/<env> vm-creation.yml

## Install kubernetes

    ansible-playbook -i inventories/<env> kubernetes.yml

## Configure kubectl client

    ansible-playbook -i inventories/<env> kube-client.yml
    kubectl config use-context <kube-context>

## Deploy kube-dns and kubernetes-dashboard

    kubectl apply -f kube-dns.yml
    kubectl apply -f kubernetes-dashboard.yml
