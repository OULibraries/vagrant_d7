# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANT_COMMAND = ARGV[0]

Vagrant.configure(2) do |config|

  ### General Vagrant Configuration #######

  # Our starting point for CentOS is Jeff Geerling's ansible base box. 
  # https://github.com/geerlingguy/packer-centos-7/
  config.vm.box = "geerlingguy/centos7" 

  # Virtualbox-specific machine configuration
  # config.vm.provider "virtualbox" do |vb|
  #   v.memory = 1024
  #   v.cpus = 2
  # end

  
  # Ansible local is broken on windows, so we bootstrap ansible with a
  # shellscript
  config.vm.provision "shell", path: "bootstrap.sh", keep_color: "True"

  if VAGRANT_COMMAND == "ssh"
    # set this to a real account
    config.ssh.username = "vagrant"  
  end
  
end
