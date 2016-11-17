Vagrant.configure("2") do |config|
	config.vm.boot_timeout = 600
	config.vm.synced_folder "Modules", "/usr/share/puppet/modules"
	
	config.vm.define "Master" do |master|
		master.vm.hostname = "Master.qac.local"
		master.vm.box = "chad-thompson/ubuntu-trusty64-gui"
		master.vm.network :public_network, :public_network => "wlan0", ip: "192.168.1.30"
		master.vm.provision :shell, path: "bootstrap_master.sh"
		master.vm.provider :virtualbox do |masterVM|
			masterVM.gui = false
			masterVM.name = "Master"
			masterVM.memory = 4096
			masterVM.cpus = 2
		end
	end
	
	config.vm.define "Agent" do |agent|
		agent.vm.hostname = "agent.qac.local"
		agent.vm.box = "chad-thompson/ubuntu-trusty64-gui"
		agent.vm.network :public_network, :public_network => "wlan0", ip: "192.168.1.31"
		agent.vm.provision :shell, path: "bootstrap_agent.sh"
		agent.vm.provider :virtualbox do |agentVM|
			agentVM.gui = false
			agentVM.name = "agent"
			agentVM.memory = 4096
			agentVM.cpus = 2
		end
	end
end