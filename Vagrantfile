# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "jessie64"
  config.vm.hostname = "nfs-test"
  config.vm.network :private_network, ip: "10.0.8.178"
  config.vm.network :forwarded_port, guest: 80, host: 8080
  config.vm.network :forwarded_port, guest: 35729, host: 35729
  config.ssh.forward_agent = true

  config.vm.synced_folder "../nfs", "/home/vagrant/nfs", mount_options: ['rw', 'vers=3', 'fsc' ,'actimeo=2', 'async'], nfs: true
  config.vm.provider :virtualbox do |vb|
    # Use VBoxManage to customize the VM. For example to change memory:
        vb.customize ["modifyvm", :id, "--memory", "2048"]
        vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        vb.customize ["modifyvm", :id, "--cpus", "2"]
        vb.customize ["modifyvm", :id, "--nictype1", "virtio"]
        vb.customize ["modifyvm", :id, "--nictype2", "virtio"]
        vb.name = "nfs-test"
  end

  config.vm.provision :ansible do |ansible|
      ansible.playbook = "test-nfs.yml"
      ansible.verbose = "v"
      ansible.inventory_path = "development"
      ansible.limit = "all"
  end

end
