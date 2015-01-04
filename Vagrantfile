# -*- mode: ruby -*-
# vi: set ft=ruby :

vm_ip='10.4.0.10'
hostname='vm01.example.com'
ram='1024'
cpus='2'

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.provider :virtualbox do |vb|
   vb.gui = ENV['VAGRANT_GUI'] || false
   vb.customize ["modifyvm", :id, "--memory", ENV['VAGRANT_MEMORY_SIZE'] || ram ]
   vb.customize ["modifyvm", :id, "--cpus",   ENV['VAGRANT_CPUS'] || cpus]
   vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
  end

  config.vm.box = "centos-7.0"
  config.vm.network :private_network, ip: vm_ip
  config.vm.hostname = hostname
  config.ssh.forward_agent = true
  config.vm.synced_folder '~/Dropbox/Projects', '/home/vagrant/Projects', :nfs => true
  config.vm.provision :shell, :inline => "/vagrant/bin/bootstrap"
end

