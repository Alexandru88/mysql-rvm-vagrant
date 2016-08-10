# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure("2") do |config|
	config.vm.box = "xenial64"
	config.vm.box_url = "https://cloud-images.ubuntu.com/xenial/current/xenial-server-cloudimg-amd64-vagrant.box"

	config.vbguest.auto_update = false if config.respond_to?(:vbguest=)

	config.vm.network :private_network, ip: "2.7.0.3"
	#config.vm.network :public_network, bridge: :dummy

	config.vm.network :forwarded_port, guest: 3000, host: 3000

	config.vm.synced_folder "../oar_contest", "/var/www/oar_contest", :mount_options => ["dmode=755","fmode=644"]

	config.vm.provider :virtualbox do |vb|
		# vb.gui = true
		vb.customize ["modifyvm", :id, "--memory", "1024", "--cpuexecutioncap", "90", "--name", "rails-dev-box"]
	end

	config.vm.provision :shell, :path => "bootstrap.sh"
	config.vm.provision :shell, :path => "bootstrap.user.sh", privileged: false
end
