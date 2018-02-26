# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "adu-test-centOS6.5-ansible"
#  config.vm.box_url = "http://developer.nrel.gov/downloads/vagrant-boxes/CentOS-6.5-x86_64-v20140110.box"
  config.vm.box_url = "CentOS-6.5-x86_64-v20140504.box"

  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end

  config.vm.network "private_network", ip: "192.168.50.6"
  config.vm.network "public_network", ip: "192.168.252.200"
  config.vm.synced_folder "../", "/var/www/html", type: "nfs"
  
  config.vm.provision :ansible do |ansible|
      ansible.playbook = "ansible/playbook.yml"
      ansible.inventory_path = "ansible/hosts"
      ansible.limit = 'all'
  end

end
