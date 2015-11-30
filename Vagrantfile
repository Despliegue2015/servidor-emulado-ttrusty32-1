# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "ubuntu/trusty32"

  # Create a private network, which allows host-only access to the machine
  # using a specific IP.
  config.vm.network "private_network", ip: "192.168.33.10"

  # Vagrant box configurations 
  config.vm.provider "virtualbox" do |v|
	v.name = "Maquina base Despliegue"
    # Increase VM Memory to resolve bug associated with MySQL 5.6 install
    # See https://github.com/fideloper/Vaprobash/issues/335#issuecomment-44913379
    v.memory = 1024
    # Use host VPN 
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  # Basic LAMP server
  config.vm.provision :shell, path: "bootstrap.sh"

  # Do not insert a fresh key
  config.ssh.insert_key = false

end
