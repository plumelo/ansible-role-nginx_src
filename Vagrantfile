# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure('2') do |config|
  config.vm.hostname = 'nginx'
  config.vm.box = 'plumelo/xenial64'

  config.ssh.forward_agent = true

  config.vm.provider :lxc do |lxc|
    lxc.container_name = 'nginx'
  end

  config.vm.provision 'ansible' do |ansible|
    ansible.playbook = 'test/purge.yml'
    # ansible.galaxy_role_file  = 'provision/galaxy.yml'
  end
end
