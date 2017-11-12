$tscript = <<TSCRIPT
wget https://raw.githubusercontent.com/TatuE/puppetInstaller/master/puppetSlaver.sh
bash puppetSlaver.sh
TSCRIPT


Vagrant.configure(2) do |config|
 config.vm.box = "bento/ubuntu-16.04"
 config.vm.network :forwarded_port, guest: 22, host: 10122, id: 'ssh'
 config.vm.provision "shell", inline: $tscript

	(1..3).each do |i|
		config.vm.define "slave-#{i}" do |slave-"#{i}"|
  	 	slave-"#{i}".vm.hostname = "slave-#{i}"
 		end

 	end
end
