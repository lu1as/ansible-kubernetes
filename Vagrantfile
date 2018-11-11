# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define :master1 do |master1|
        master1.vm.hostname = "kube-master1"
        
        # Template
        master1.vm.box = "generic/debian9"
    
        # Domain Specific Options
        master1.vm.provider :libvirt do |domain|
            domain.memory = 2048
            domain.cpus = 1
        end
    
        # Interfaces
        master1.vm.network :private_network, :ip => '192.168.123.10'
    end

    config.vm.define :minion1 do |minion1|
        minion1.vm.hostname = "kube-minion1"
        
        # Template
        minion1.vm.box = "generic/debian9"
    
        # Domain Specific Options
        minion1.vm.provider :libvirt do |domain|
            domain.memory = 2048
            domain.cpus = 1
        end
    
        # Interfaces
        minion1.vm.network :private_network, :ip => '192.168.123.11'
    end
    
    # Options for libvirt vagrant provider.
    config.vm.provider :libvirt do |libvirt|
    
        # A hypervisor name to access. Different drivers can be specified, but
        # this version of provider creates KVM machines only.
        libvirt.driver = "kvm"
    
        # The name of the server, where libvirtd is running.
        libvirt.host = ""
    
        # If use ssh tunnel to connect to Libvirt.
        libvirt.connect_via_ssh = false
    
        # The username and password to access Libvirt. Password is not used when
        # connecting via ssh.
        #libvirt.username = "root"
        #libvirt.password = "secret"
    
        # Libvirt storage pool name, where box image and instance snapshots will
        # be stored.
        libvirt.storage_pool_name = "default"
    
        # Set a prefix for the machines that's different than the project dir name.
        #libvirt.default_prefix = ''
    end

    # Disable nfs
    config.vm.synced_folder '.', '/vagrant', disabled: true
end
