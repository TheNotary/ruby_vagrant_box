# Rails on Vagrant

This is just a quick script for getting a dev a rails env.  After the VM is setup, that can do a git clone and pull in what ever project it is they're working on.  


## Install

Only a couple things need to be installed in order to setup VMs.  All other installations take place within the underlining VM and won't effect the dev's system stability.  


```bash
$  sudo apt-get install vagrant
```


## Usage

Now that vagrant is installed, clone this repo into  a directory where you'd like the software configured.  
  

```
$  git clone https://github.com/TheNotary/ruby_vagrant_box new_rails_project
```

Now you get to build the VM on your local system.  

```
$  cd new_rails_project
   vagrant up
```

When that command completes, you should be able to ssh into your new vagrant box and clone the rails app you'll be working on and start hacking away.  

```
$  vagrant ssh

(vagrant) $  git clone https://github.com/EFForg/action-center-platform.git
(vagrant) $  cd action-center-platform
             # Install a different version of ruby if instructed in terminal

(vagrant) $  bundle install
(vagrant) $  rails s
```
