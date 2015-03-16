# -*- mode: ruby -*-
# vi: set ft=ruby :


CONFIG = File.join(File.dirname(__FILE__), "config.rb")

# Defaults for config options defined in config.rb
$num_minions = 1
$enable_serial_logging = (ENV['SERIAL_LOGGING'].to_s.downcase == 'true')
$vm_gui = (ENV['GUI'].to_s.downcase == 'true')
$vm_memory = ENV['NODE_MEM'] || 1024
$vm_cpus = ENV['NODE_CPUS'] || 1

if File.exist?(CONFIG)
  require CONFIG
end


# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  config.vm.box         = "imikushin/rancheros-cluster"
  config.vm.box_version = "0.1.2"
  config.ssh.username   = "rancher"

  config.vm.provider "virtualbox" do |vb|
     vb.check_guest_additions = false
     vb.functional_vboxsf     = false
  end

  config.vm.synced_folder ".", "/vagrant", disabled: true

  (1..($num_minions + 1)).each do |i|
    hostname = "node-%02d" % i

    config.vm.define vmName = hostname do |node|
      ## Setting hostname not supported yet
      # node.vm.hostname = vmName

      node.vm.provider "virtualbox" do |vb|
        vb.gui = $vm_gui
        vb.memory = $vm_memory
        vb.cpus = $vm_cpus
      end

      ## Configure network not supported yet. using `auto_config: false`
      node.vm.network :private_network, type: :dhcp, auto_config: false

      node.vm.provision "file", source: "src/node-ip.sh", destination: "/home/rancher/node-ip.sh"
      node.vm.provision "shell", inline: "echo NODE_IP=`/home/rancher/node-ip.sh`", run: "always"

      ## Shared folders not supported yet
      node.vm.synced_folder ".", "/vagrant", disabled: true

    end
  end
end
