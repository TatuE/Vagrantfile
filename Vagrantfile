# vim: filetype=ruby


$tscript = <<TSCRIPT
echo "172.28.171.19 pmaster.erkinjnutti.me" |sudo tee --append /etc/hosts
wget https://raw.githubusercontent.com/TatuE/puppetInstaller/master/puppetSlaver.sh
bash puppetSlaver.sh
TSCRIPT

Vagrant.configure(2) do |config|
config.vm.box = "bento/ubuntu-16.04"

        (1..3).each do |i|
                slave = "slave#{i}"
                config.vm.define slave do |slave|
                slave.vm.hostname = "slave#{i}"
                slave.vm.network :forwarded_port, guest: 22, host: 50000+i, id: 'ssh'
                end
        end
end




