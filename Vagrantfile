# -*- mode: ruby -*-
# vi: set ft=ruby :
# ============================================================================
# Vagrantfile — WordPress con Ansible
# Proyecto transversal FinTech Solutions S.A. / TechOps Solutions
# ============================================================================

Vagrant.configure("2") do |config|
  config.vm.box = "generic/ubuntu2204"

  config.vm.network "private_network", ip: "192.168.56.20"
  config.vm.network "forwarded_port", guest: 8080, host: 8085
  config.vm.network "forwarded_port", guest: 443, host: 8443

  config.vm.provider "libvirt" do |lv|
    lv.memory = 2048
    lv.cpus   = 2
  end

  config.vm.provider "virtualbox" do |vb|
    vb.memory = 2048
    vb.cpus   = 2
  end

  # Aprovisionamiento con Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook       = "playbook.yml"
    ansible.compatibility_mode = "2.0"
  end
end
