# -*- mode: ruby -*-
# vi: set ft=ruby :

members = {
  #  Name       #, 1ST_IP
  'node'   => [ 3,    101 ],
}
PREFIX          = "10.10.10"

Vagrant.configure("2") do |config|

  config.vm.box = "rancherio/rancheros"

  members.each do |name, (count, ipstart)|
    (1..count).each do |i|
      config.vm.define member = "%s-%02d" % [name, i] do |m|
        m.vm.synced_folder ".", "/vagrant", disabled: true
        ip = "%s.%02d" % [PREFIX, ipstart+i-1]
        m.vm.network "private_network", ip: ip, auto_config: false, :adapter => 2
        m.vm.provision "shell", inline: <<-EOF
ros config merge <<ROS
hostname: #{member}

rancher:
  network:
    interfaces:
      eth1:
        match: eth1
        address: #{ip}/24
ROS
        EOF
        m.vm.provision "shell", inline: "sudo reboot"
      end
    end
  end
end
