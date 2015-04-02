# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|

  config.vm.define "dbasm" do |dbasm|

    dbasm.vm.box = "hajee/centos-5.10-x86_64"
    dbasm.vm.box_url = "https://vagrantcloud.com/hajee/boxes/centos-5.10-x86_64"
    

    dbasm.vm.synced_folder ".", "/vagrant", :mount_options => ["dmode=777","fmode=777"]

    dbasm.ssh.forward_agent = true
    dbasm.ssh.forward_x11 = true
    dbasm.vm.hostname = "ora12asm"

    dbasm.vm.provider :virtualbox do |vb|

      # vb.gui = true
      vb.customize ["modifyvm", :id, "--memory", "2048"]
      vb.customize ["modifyvm", :id, "--name", "dbasm"]
      vb.customize ["modifyvm", :id, "--cpus", "2"]
      vb.customize ["modifyvm", :id, "--ioapic", "on"]
      vb.customize ["modifyvm", :id, "--nic3", "intnet"]
    end

    dbasm.vm.network :private_network, ip: "172.16.10.20"
    #dbasm.vm.network "public_network", ip: "192.168.0.27"
    dbasm.vm.network :forwarded_port, guest: 22, host: 1234
    #precise32.vm.network :hostonly, "192.168.1.27"    
    dbasm.ssh.forward_agent = true
    dbasm.ssh.forward_x11 = true


    dbasm.vm.provision :shell, :path => "provision.sh"

  end




  


end
