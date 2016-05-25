# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure(2) do |config|
  #config.vm.box = 'ubuntu/trusty64'
  config.vm.box = 'https://s3.amazonaws.com/jana-vagrant-images/ipython-20160525.box'

  config.vm.provider :virtualbox do |vb|
    vb.memory = '2048'
  end

  config.vm.network :forwarded_port, guest: 8888, host: 8888

  config.vm.synced_folder '../ipython_notebooks', '/home/vagrant/ipython_notebooks'

  config.vm.provision :shell, inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y python-numpy python-scipy python-matplotlib ipython \
                            ipython-notebook python-pandas python-sympy python-nose \
                            python-pip libfreetype6-dev pkg-config libncurses5-dev \
                            openjdk-7-jdk libffi-dev openssl build-essential libssl-dev \
                            python-dev

    cd ipython_notebooks

    sudo pip install pip --upgrade

    sudo -H pip install -r requirements.txt

  SHELL

  config.vm.provision :shell, run: 'always', privileged: false, inline: <<-SHELL
    cd ipython_notebooks

    sudo -H pip install -r requirements.txt

    ipython profile create jana
    rm -f ~/.ipython/profile_jana/startup/*
    ln -s ~/ipython_notebooks/cookbook/profile_jana/startup/* ~/.ipython/profile_jana/startup/

    ipython notebook --profile=jana --ip=0.0.0.0 --no-browser &

    echo "\n"
    echo "\n"
    echo "*******************************************************************"
    echo "You're all set!  Please visit http://localhost:8888 in your browser!"
  SHELL
end
