# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|

  ### General Vagrant Configuration #######
  
  # First, get settings from my-vars.yml
  require 'yaml'
  myvarsfile = File.dirname(__FILE__)+'/my-vars.yml'
  myvars = YAML.load_file(myvarsfile) # TODO should probably error out if my-vars DNE
  
  # Our starting point for CentOS is Jeff Geerling's ansible base box. 
  # https://github.com/geerlingguy/packer-centos-7/
  config.vm.box = "geerlingguy/centos7" 

  # Virtualbox-specific machine configuration
  # config.vm.provider "virtualbox" do |vb|
  #   v.memory = 1024
  #   v.cpus = 2
  # end

  # # Do control machine tasks first
  # config.vm.provision "ansible_local" do |ansible|
  #   ansible.provisioning_path = "/vagrant"
  #   ansible.playbook = "control-machine.yml"
  # end

  ### Application Specific Setup #########

  # unless we're not in vagrant mode, mount the /srv folder so that we
  # can remount it with the right permissions later

  unless myvars.key?("environment_name") && "vagrant" != myvars["environment_name"]
    config.vm.synced_folder "./srv/", "/srv/"
  end
  
  # Temorary workaround because Windows
  config.vm.provision "shell", path: "bootstrap.sh"

    
  # # Then do d7 stuff
  # config.vm.provision "ansible_local" do |ansible|
  #   ansible.provisioning_path = "/vagrant"
  #   ansible.galaxy_role_file = "requirements.yml"
  #   ansible.playbook = "vagrant.yml"
  # end
  
end
