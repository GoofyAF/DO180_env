# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Base VM OS configuration.
  config.vm.box = "generic/rhel9"
  config.ssh.insert_key = false
  config.vm.synced_folder '.', '/vagrant', disabled: true

  # General VirtualBox VM configuration.
  config.vm.provider :virtualbox do |v|
    v.memory = 512
    v.cpus = 1
    v.linked_clone = true
    v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    v.customize ["modifyvm", :id, "--ioapic", "on"]
  end

  # utility.
  config.vm.define "DO180_utility" do |utility|
    utility.vm.hostname = "utility.lab.example.com"
    utility.vm.network :private_network, ip: "192.168.56.50"
    utility.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # workstation.
  config.vm.define "DO180_workstation" do |workstation|
    workstation.vm.hostname = "workstation.lab.example.com"
    workstation.vm.network :private_network, ip: "192.168.56.51"
    workstation.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # registry.
  config.vm.define "DO180_registry" do |registry|
    registry.vm.hostname = "registry.ocp4.example.com"
    registry.vm.network :private_network, ip: "192.168.56.52"
    registry.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # master
  config.vm.define "DO180_master" do |master|
    master.vm.hostname = "master01.ocp4.example.com"
    master.vm.network :private_network, ip: "192.168.56.53"
    master.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # idm.
  config.vm.define "DO180_idm" do |idm|
    idm.vm.hostname = "idm.ocp4.example.com"
    idm.vm.network :private_network, ip: "192.168.56.54"
    idm.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end

  # registry.
  config.vm.define "DO180_registry" do |registry|
    registry.vm.hostname = "registry.ocp4.example.com"
    registry.vm.network :private_network, ip: "192.168.56.55"
    registry.vm.provider :virtualbox do |v|
      v.customize ["modifyvm", :id, "--memory", 512]
    end
  end
  # Ansible provisioning.
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "configure.yml"
    #ansible.become = true
    ansible.limit = "all"
    ansible.extra_vars = {
      ansible_python_interpreter: "/usr/bin/python3",
      ansible_user: 'vagrant',
      ansible_ssh_private_key_file: "~/.vagrant.d/insecure_private_key",
    }  
  end
end