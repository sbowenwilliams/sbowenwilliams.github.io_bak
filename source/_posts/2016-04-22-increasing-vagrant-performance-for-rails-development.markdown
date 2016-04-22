---
layout: post
title: "Increasing Vagrant Performance for Rails Development"
date: 2016-04-22 11:48:07 -0500
comments: true
categories: 
---
# Increased Vagrant Performance for Rails Development

Vagrant is awesome. It kicks ass. It's the cat's pajamas. It allows you to modularize dependencies that are specific to your app. It makes my life better is nearly every conceivable way and it even makes me a better lover.

But for all the pros Vagrant is still a virtual machine, and virtual machines are slow. But don't fret, there are optimizations we can make to speed up your rails app within Vagrant.

## Disable Log files
Rails likes to write stuff down. A lot. When I cracked open my own `development.log` file it had nearly half a million lines. That's lots of wasted cycles waiting to write to a file. I'm going to share a dirty secret: I've never used the development log file for debugging. So let's get rid of it.
Within `config/development.rb` add:
```
ProjectName::Application.configure do
    config.logger = ActiveSupport::Logger.new(nil)
end
```
Where `ProjectName` is the, well, name of your project.

This still provides output for the console and seems to work well with other logging gems.
        
## Use The NFS
VirtualBox uses it's own protocol to share files between the host and Vagrant by default. NFS, in most cases, will be much faster. Luckily switching over is dead simple. Fire up your favorite text editor and add the following to your Vagrantfile:
```
# Required, pick a local IP
config.vm.network :private_network, ip: '192.168.x.x'
config.vm.synced_folder '.', '/vagrant', nfs: true
```

## Just one core please
More is not always... more. It has been proven [several](https://ruin.io/2014/benchmarking-virtualbox-multiple-core-performance/)[times](http://www.mihaimatei.com/virtualbox-performance-issues-multiple-cpu-cores/) (okay, a couple times) that adding multiple cores actually reduces VirtualBox performance.
Once again edit your Vagrantfile to include the following line:

```
vb.customize ["modifyvm", :id, "--cpus", "1"]
```

## Final Thoughts
There are definitely other tweaks out there that could increase performance, but the above are what have the biggest impact for me. The jury is still out on an optimal amount of RAM, but the consensus is somewhere between 1/4 and 1/2 total system memory. I encourage experimetation. 
