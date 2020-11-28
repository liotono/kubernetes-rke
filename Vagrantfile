# -*- mode: ruby -*-
# vi: set ft=ruby :
#

ENV['VAGRANT_NO_PARALLEL'] = 'yes'

MASTER_NODES = 3
WORKER_NODES = 6

IPSTART_MASTER = 10
IPSTART_WORKER = 30

Vagrant.configure("2") do |config|

  # For vagrant hostmanager plugin
  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.ignore_private_ip = false

  # Image to use
  config.vm.box = "generic/ubuntu1604"
  config.vm.box_check_update = false

  # Creating the master nodes
  (1..MASTER_NODES).each do |i|
    config.vm.define "k8s-master-#{i}" do |box|
      box.vm.hostname = "k8s-master-#{i}"
      box.vm.synced_folder ".", "/vagrant", disabled: true
      box.vm.network :private_network, ip: "192.168.5.#{IPSTART_MASTER + i}", :netmask => "255.255.255.0"
      box.vm.provider :libvirt do |domain|
        domain.memory = 3072
        domain.cpus = 2
      end
    end
  end

  # Creating the slave nodes
  (1..WORKER_NODES).each do |i|
    config.vm.define "k8s-worker-#{i}" do |box|
      box.vm.hostname = "k8s-worker-#{i}"
      box.vm.synced_folder ".", "/vagrant", disabled: true
      box.vm.network :private_network, ip: "192.168.5.#{IPSTART_WORKER + i}", :netmask => "255.255.255.0"
      box.vm.provider :libvirt do |domain|
        domain.memory = 3072
        domain.cpus = 1
      end
    end
  end

end
