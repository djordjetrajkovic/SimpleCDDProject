$script = <<-'SCRIPT'
apt-get -y update
apt-get -y install simple-cdd
SCRIPT

$script1 = <<-'SCRIPT'
mkdir /home/vagrant/my-cdd
cp -r /vagrant/profiles /home/vagrant/my-cdd && cp /vagrant/simple-cdd.conf /home/vagrant/my-cdd
#chown -R vagrant:vagrant /home/vagrant/my-cdd
cd /home/vagrant/my-cdd
build-simple-cdd --conf simple-cdd.conf
SCRIPT

$script2 = <<-'SCRIPT'
cp /home/vagrant/my-cdd/images/*.iso /vagrant
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "bento/debian-10"
  config.vm.hostname = "deb4ccd"
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 1
    vb.memory = "2048"
    vb.name = "DebianMaker"
  end
  config.vm.provision "shell", inline: $script
  config.vm.provision "shell", inline: $script1, privileged: false
  config.vm.provision "shell", inline: $script2
end
