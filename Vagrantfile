# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  project_name = 'vagrant_django'
  $memory = 1024
  $cpus = 2

  config.vm.provider :virtualbox do |vb|
    config.vm.box = "hashicorp/precise64"
    vb.memory = $memory
    vb.cpus = $cpus
  end

  config.vm.provider :parallels do |prl|
    config.vm.box = "parallels/ubuntu-14.04"
    prl.memory = $memory
    prl.cpus = $cpus
    prl.update_guest_tools = true
  end

  config.vm.network "forwarded_port", guest: 8000, host: 8000

  config.vm.synced_folder ".", "/home/vagrant/#{project_name}"

  config.vm.provision "shell", path: "install_packages.sh", :args => "#{project_name}"
end
