# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  
  config.vm.box = "ubuntu14.04"
  config.vm.network "private_network", type: "dhcp"

  config.vm.define "influx" do |influx|
	config.vm.network "private_network", ip: "192.168.52.4"
  	influx.vm.network "forwarded_port", guest: 8083, host: 8083
   	influx.vm.network "forwarded_port", guest: 8086, host: 8086
  end

  config.vm.define "collectd" do |collectd|
	config.vm.network "private_network", ip: "192.168.52.5"
  end
  
  config.vm.define "nagios" do |nagios|
	config.vm.network "private_network", ip: "192.168.52.6"
        nagios.vm.network "forwarded_port", guest: 80, host:8090
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "provisioning/site.yml"
  end

end
