# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|

  # Every Vagrant virtual environment requires a box to build off of.
  config.vm.box = "win10x64Pro"
  config.vm.box_url = "http://1drv.ms/23vSyQi"

  config.vm.guest = :windows
  config.vm.communicator = "winrm"
  config.vm.boot_timeout = 600
  config.vm.graceful_halt_timeout = 600

  config.vm.network :forwarded_port, guest: 3389, host: 3389
  config.vm.network :forwarded_port, guest: 5985, host: 5985, id: "winrm", auto_correct: true

  config.vm.provider "virtualbox" do |vm|
      vm.name = "vagrant-pc"
      vm.gui = true
      vm.cpus = 2
      vm.memory = 2048
  end
end
