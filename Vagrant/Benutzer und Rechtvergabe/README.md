Vagrant.configure(2) do |config|
  config.vm.box = "ubuntu/xenial64"
  config.vm.provider "virtualbox" do |vb|
end

config.vm.provision "shell", inline: <<-SHELL
sudo useradd Ferzana
sudo useradd Yang
sudo useradd Laura
sudo groupadd IT
sudo groupadd KV
sudo groupadd HR
sudo usermod -a -G IT Ferzana
sudo usermod -a -G KV Yang
sudo usermod -a -G HR Laura
sudo touch file1.txt
SHELL
end
