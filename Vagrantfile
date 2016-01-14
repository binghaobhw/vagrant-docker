# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV["VAGRANT_DEFAULT_PROVIDER"] = "docker"

$script = <<SCRIPT
echo hi
SCRIPT

Vagrant.configure(2) do |config|
  config.vm.define "ltp-server" do |l|
    l.vm.provider "docker" do |d|
      d.name = "ltp-server"
      d.image = "ubuntu:14.04"
      d.ports = ["12345:12345"]
      d.vagrant_vagrantfile = "./docker-host.vagrant"
      d.remains_running = true
      d.cmd = ["top"]
    end

    l.vm.provision "shell", inline: $script
  end
end
