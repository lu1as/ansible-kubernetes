# ansible-kubernetes

ansible playbooks to build a kubernetes cluster

Compatible with:
- Fedora Atomic 29
- Raspbian 9
- Debian 9 (Stretch)

Hypervisor support for Debian (libvirt with KVM)

## Setup

- create an inventory in `inventories/` based on the sample
- for virtual machines create a `cloud-config.yml` file in `vars/`
- IMPORTANT: Inventory names will be used as hostnames. For example inventory name `master1` and kube_domain `kube.example.com` would result to `master1.kube.example.com`

## Create virtual machines

    ansible-playbook -i inventories/<env> vm-creation.yml

## Install kubernetes

    ansible-playbook -i inventories/<env> kubernetes.yml

### Use with vpn network

If you want to use an existing vpn network set `flanneld_host_interface` to your vpn interface and add the variable `internal_ip` pointing to the vpn interface address.
Wireguard needs a special patch, which you can apply by setting `flanneld_over_wireguard` to `true`.

## Configure kubectl client

    ansible-playbook -i inventories/<env> kube-client.yml
    kubectl config use-context <kube-context>

## Backup and restore

Backups will be created on first master node at `backup_dir` which is `/mnt/backup` by default.
If you want to use a nfs share at this location, set `backup_nfs_share` to your share.
For example: `nfs-server:/kubernetes-backup`

### Pki backup

To enable pki backup set `pki_enable_backup` to `true`.
Restore from backup: `--extra-vars="pki_restore_backup=true"`
