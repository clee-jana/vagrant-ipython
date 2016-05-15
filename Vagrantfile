# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/trusty64"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.network "forwarded_port", guest: 8888, host: 9888

  config.vm.synced_folder "../ipython_notebooks", "/home/vagrant/ipython_notebooks"

  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo -Y apt-get install python-numpy python-scipy python-matplotlib ipython \
                            ipython-notebook python-pandas python-sympy python-nose \
                            python-pip
    cd ipython_notebooks

    ipython profile create jana
    rm -f ~/.ipython/profile_jana/startup/*
    ln -s ~/ipython_notebooks/cookbook/profile_jana/startup/* ~/.ipython/profile_jana/startup/

    pip install -r requirements.txt
  SHELL
end
