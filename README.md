# IPython Notebook

* Access the graphite web console at [http://localhost:8888](http://localhost:8888)

## Installation Instructions

* Download [Vagrant](http://vagrantup.com)
* Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* Start your vagrant image with `vagrant up` and SSH in with `vagrant ssh`
* Installation assumes that the Jana `ipython_notebook` repo is
  located at the directory tree level as this repo.

```
# example
+ userhome
  + jana
    + ipython_notebooks
    + vagrant-ipython (this repo)
```

## Starting Vagrant

```
# From this repo's root directory.
# The first time will take a few minutes as it downloads the image and
# installs the necessary libraries
$> vagrant up

# to resume a suspended instance
$> vagrant resume

# ssh into the isntance
$> vagrant ssh
```

## Restarting Vagrant

Restarting the Vagrant instance will reinstall the python requirements
and restart the ipython notebook server.
```
$> vagrant reload
```

## Stopping the instance
```
# standby
$> vagrant suspend

# shutdown
$> vagrant halt

# delete the instance to start over. please note you will lose the contents of the vagrant box. synced folders are safe because they are on the host vm.
$> vagrant destroy
```
