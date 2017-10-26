# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.boot_timeout=600
  config.vm.define "node0" do |node0|
    node0.vm.box = "bento/ubuntu-16.04"
    node0.vm.network "private_network", ip: "172.30.30.10"
    node0.vm.hostname = "node0"
    node0.vm.provider "virtualbox" do |vbnode0|
      vbnode0.memory = "2048"
      vbnode0.cpus = "2"
    end
    node0.vm.provision "file", source: "./sources.list", destination: "/tmp/sources.list"
    node0.vm.provision "shell", inline: "sudo cp /tmp/sources.list /etc/apt/sources.list"
    node0.vm.provision "shell", inline: " sudo route add -net 10.96.0.0 netmask 255.255.0.0 dev enp0s8"
  end

  config.vm.define "node1" do |node1|
    node1.vm.box = "bento/ubuntu-16.04"
    node1.vm.network "private_network", ip: "172.30.30.11"
    node1.vm.hostname = "node1"
    node1.vm.provider "virtualbox" do |vbnode1|
      vbnode1.memory = "2048"
      vbnode1.cpus = "2"
    end
    node1.vm.provision "file", source: "./sources.list", destination: "/tmp/sources.list"
    node1.vm.provision "shell", inline: "sudo cp /tmp/sources.list /etc/apt/sources.list" 
    node1.vm.provision "shell", inline: " sudo route add -net 10.96.0.0 netmask 255.255.0.0 dev enp0s8"
  end

  config.vm.box_check_update = false
end
