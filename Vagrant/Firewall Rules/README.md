Vagrant.configure(2) do |config|
config.vm.box = "ubuntu/xenial64"
config.vm.provider "virtualbox" do |vb|
end

config.vm.provision "shell", inline: <<-SHELL
sudo ufw allow 80/tcp
vagrant ssh web
sudo ufw allow from any to any port 22
sudo ufw allow from any to any port 3306
sudo ufw --force enable
SHELL
end
