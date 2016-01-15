# -*- mode: ruby -*-
# vi: set ft=ruby :

# A dummy plugin for DockerRoot to set hostname and network correctly at the very first `vagrant up`
module VagrantPlugins
  module GuestLinux
    class Plugin < Vagrant.plugin("2")
      guest_capability("linux", "change_host_name") { Cap::ChangeHostName }
      guest_capability("linux", "configure_networks") { Cap::ConfigureNetworks }
    end
  end
end

Vagrant.configure(2) do |config|
  config.vm.box = "ailispaw/docker-root"
  config.vm.box_version = "1.2.8"
  config.vm.provider "virtualbox"
  config.vm.define "docker-host"
  config.vm.hostname = "docker-host"
  config.vm.synced_folder ".", "/vagrant"

  # for NFS synced folder
  # config.vm.network "private_network", ip: "192.168.33.10"
  # config.vm.synced_folder ".", "/vagrant", type: "nfs", mount_options: ["nolock", "vers=3", "udp"]

  # for RSync synced folder
  # config.vm.synced_folder ".", "/vagrant", type: "rsync", rsync__args: ["--verbose", "--archive", "--delete", "--copy-links"]

  #if Vagrant.has_plugin?("vagrant-triggers") then
  #  config.trigger.after [:up, :resume] do
  #    info "Adjusting datetime after suspend and resume."
  #    run_remote "sudo sntp -4sSc pool.ntp.org; date"
  #  end
  #end

  ## Adjusting datetime before provisioning.
  #config.vm.provision :shell, run: "always" do |sh|
  #  sh.inline = "sntp -4sSc pool.ntp.org; date"
  #end

  #config.vm.provision :docker do |d|
  #  d.pull_images "solr:5.3.1"
  #  d.run "--name solr -d -p 8983:8983 -t solr:5.3.1"
  #end

  #config.vm.network :forwarded_port, guest: 8983, host: 8983
end
