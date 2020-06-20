# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure("2") do |c|

  c.vm.box = "bento/ubuntu-18.04"
  c.vm.synced_folder ".", "/vagrant"

  c.vm.provider :hyperv do |v|
    v.memory = 6442
    v.cpus = 3
  end

  c.vm.define :awx do |awx|
    awx.vm.provision :ansible_local do |ansible|
      ansible.compatibility_mode = "2.0"
      ansible.playbook = "playbook.yml"
      ansible.extra_vars = {ansible_python_interpreter: "/usr/bin/python3"}
      ansible.become = true
    end
  end
end
