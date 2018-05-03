# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

  # VM box
  config.vm.box = "ubuntu/xenial64"

  if Vagrant.has_plugin?("vagrant-timezone")
    config.timezone.value = :host
  end

  # Share an additional folder to the guest VM.
  config.vm.network "private_network", type: "dhcp"
  config.vm.synced_folder ".", "/home/vagrant/shared_data/", type: "nfs"

  # Please modify this to your own liking:
  config.vm.provider "virtualbox" do |v|
   v.name = "inf102vm"
   v.cpus = "1"
   v.memory = "4096"
   v.gui = false
  end

  config.vm.provision "languages", type:"shell", path: "provision/dependencies.sh"
  config.vm.provision "setup-node", privileged: false, type:"shell", path: "provision/setup-node.sh"

end
