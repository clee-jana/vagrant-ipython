# IPython Notebook

* Access the graphite web console at [http://localhost:8888](http://localhost:8888)

## Installation Instructions

* Download [Vagrant](http://vagrantup.com)
* Install [VirtualBox](https://www.virtualbox.org/wiki/Downloads)
* Installation assumes that the Jana `ipython_notebook` repo is
  located at the directory tree level as this repo.
* Start your vagrant image with `vagrant up` and SSH in with `vagrant ssh`.
  This will download a fairly large file (2 GB) to your computer and
  could take some time. I had trouble getting this to work in the office
  reliably and it would disconnect the download. It took 3 tries to
  download the file for me.
* If it completed successfully, you'll see the line:
```
You're all set! Please visit http://localhost:8888 in your browser!
```

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
