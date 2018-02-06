# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = "bento/centos-7.2"
  config.vm.hostname = "sakura7.localhost"
  config.vm.network "forwarded_port", guest: 80, host: 8080
  config.ssh.forward_agent = true
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provision/vagrant.yml"
    ansible.sudo = true
    ansible.verbose = "v"
    ansible.extra_vars = {vagrant: true}
    ansible.raw_arguments = ['--check']
  end
end
