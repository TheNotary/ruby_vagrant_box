# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"
  # config.vm.box_url = "https://vagrantcloud.com/hashicorp/boxes/trusty64/versions/1.0.0/providers/virtualbox.box"
  config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-amd64-vagrant-disk1.box"
  # Forward the Rails server default port to the host
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.ssh.username = "vagrant"

  config.vm.synced_folder "dev/", "/home/vagrant/dev"

  # If true, then any SSH connections made will enable agent forwarding.
  # Default value: false
  config.ssh.forward_agent = true

  config.vm.provider :virtualbox do |v|

    # Increase memory allocation to 2GB
    v.customize ["modifyvm", :id, "--memory", "2048"]

    # Sync time every 5 seconds with host so the ralis code reloader works
    v.customize ["guestproperty", "set", :id, "--timesync-threshold", 5000]
  end

  config.vm.provision "shell", privileged: false, inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y vim git nodejs postgresql curl libmysqlclient-dev imagemagick

    gpg --keyserver hkp://keys.gnupg.net --recv-keys 409B6B1796C275462A1703113804BB82D39DC0E3

    sudo su vagrant
    \\curl -sSL https://get.rvm.io | bash -s stable --ruby

    mkdir /home/vagrant/dev

    # sudo su vagrant
    # rvm group add rvm "vagrant"
  SHELL

end
