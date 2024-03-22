# -*- mode: ruby -*-
# vim: set ft=ruby :
#Path to HDD on host

Vagrant.configure(2) do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
    v.cpus = 1
  end

  config.vm.define "node1" do |host|
    host.vm.box = "debian/bullseye64"
    host.vm.box_version = "11.20230615.1"
    host.vm.hostname = "node1"
    host.vm.network "private_network",
                     ip: "192.168.50.10",
                     adapter: 2
  end
 
  config.vm.define "node2" do |host|
    host.vm.box = "debian/bullseye64"
    host.vm.box_version = "11.20230615.1"
    host.vm.hostname = "node2"
    host.vm.network "private_network",
                     ip: "192.168.50.11",
                    adapter: 2
  end

  config.vm.define "barman" do |host|
    host.vm.box = "debian/bullseye64"
    host.vm.box_version = "11.20230615.1"
    host.vm.hostname = "barman"
    host.vm.network "private_network",
                     ip: "192.168.50.12",
                     adapter: 2
    host.vm.provision "ansible" do |ansible|
      ansible.playbook = "ansible/play.yml"
      ansible.inventory_path = "ansible/hosts"
      ansible.host_key_checking = "false"
      ansible.limit = "all"
    end
 
  end

end
