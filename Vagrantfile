# modified from a script made by Tero Karvinen 
# http://terokarvinen.com/2017/provision-multiple-virtual-puppet-slaves-with-vagrant


$tscript = <<TSCRIPT
echo "46.101.196.129 pmaster.erkinjuntti.me pmaster" |sudo tee --append /etc/hosts
wget https://raw.githubusercontent.com/TatuE/puppetInstaller/master/puppetSlaver.sh
bash puppetSlaver.sh
TSCRIPT

Vagrant.configure(2) do |config|
config.vm.box = "minimal/trusty64"
config.vm.boot_timeout = 900    
config.vm.provision "shell", inline: $tscript        

        (1..3).each do |i|
                slave = "slaveA#{i}"
                config.vm.define slave do |slave|
                slave.vm.hostname = "slaveA#{i}"
                slave.vm.network :forwarded_port, guest: 22, host: 62000+i, id: 'ssh'
                end
        end
end




