# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "geerlingguy/ubuntu1604"
  config.ssh.insert_key = false
  config.vm.synced_folder ".", "/vagrant", disabled: true
  config.vm.network :forwarded_port, guest: 54444, host: 4567
  config.vm.provider :virtualbox do |v|
    v.memory = 256
    v.linked_clone = true
  end

  # Application server 1.
  config.vm.define "di-node-app" do |app|
    app.vm.hostname = "di-node-app.dev"
    app.vm.network :private_network, ip: "192.168.60.10"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml" 
  end
end
