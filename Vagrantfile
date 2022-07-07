Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |vb|
    # vb.customize [
    #   "modifyvm", :id,
	#   "--memory", "4096",
	#   "--cpus", "2"
    # ]
    vb.memory = 4096
    vb.cpus = 2
	vb.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
    vb.customize ["modifyvm", :id, "--natdnsproxy1", "on"]
  end
  config.vm.box = "generic/ubuntu2004"
  config.vm.box_check_update = false
  config.vm.synced_folder ".", "/vagrant"
  config.vm.network "forwarded_port", guest: 3000, host: 3000
  config.vm.provision "ansible_local" do |ansible|
    ansible.playbook = "playbook.yml"
  end
end
