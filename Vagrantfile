# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.box = "ubuntu/bionic64"

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "site.yml"
    ansible.groups = {
      "routers" => ["er1", "gw1"],
    }
  end

  config.vm.define "er1" do |r1|
    r1.vm.host_name = "er1"
    r1.vm.network "private_network",
        auto_config: false,
        virtualbox__intnet: "backbone"
  end

  config.vm.define "gw1" do |r2|
    r2.vm.host_name = "gw1"
    r2.vm.network "private_network",
        auto_config: false,
        virtualbox__intnet: "backbone"
  end

end
