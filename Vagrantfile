# -*- mode: ruby -*-
# vi: set ft=ruby :

require 'yaml'

vagrantConfig = YAML.load_file 'Vagrantfile.config.yml'

Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/vivid64"
  config.vm.network "private_network", ip: vagrantConfig['ip']

  # Mount local "~/Code-vagrant/magento2-demo/" path into box's "/vagrant-magento2-demo/" path
  config.vm.synced_folder
    vagrantConfig['synced_folder']['host_path']
    vagrantConfig['synced_folder']['guest_path'], owner: "vagrant", group: "www-data", mount_options: ["dmode=775, fmode=664"]

  # VirtualBox specific settings
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "2048"
    vb.cpus = 2
  end

  # <provisioner here>
end
