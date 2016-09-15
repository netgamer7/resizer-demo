# This guide is optimized for Vagrant 1.7 and above.
# Although versions 1.6.x should behave very similarly, it is recommended
# to upgrade instead of disabling the requirement below.
Vagrant.require_version ">= 1.8.5"

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/xenial64"

  config.vm.define "web"
  config.vm.define "redis"
  config.vm.define "worker1"
  config.vm.define "worker2"

  config.hostmanager.enabled = true
  config.hostmanager.manage_host = true
  config.hostmanager.manage_guest = true
  config.hostmanager.ignore_private_ip = false
  config.hostmanager.include_offline = true

  config.ssh.username = "ubuntu"
  config.ssh.insert_key = true

  config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = "2"
  end

  config.vm.provision :ansible do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "ansible/playbook.yml"
    ansible.inventory_path = "ansible/staging"
  end
end
