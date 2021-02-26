$script1 = <<-'SCRIPT'
apt-get -y update
apt-get -y install simple-cdd
SCRIPT

$script2 = <<-'SCRIPT'
mkdir /home/vagrant/my-cdd
cp -r /vagrant/profiles /home/vagrant/my-cdd && cp /vagrant/simple-cdd.conf /home/vagrant/my-cdd

SCRIPT

$script3 = <<-'SCRIPT'
chmod +x /home/vagrant/my-cdd/profiles/x-basic.postinst
SCRIPT

$script4 = <<-'SCRIPT'
cd /home/vagrant/my-cdd
build-simple-cdd --conf simple-cdd.conf
mv /home/vagrant/my-cdd/images/*.iso /vagrant
SCRIPT

Vagrant.configure("2") do |config|
  config.vm.box = "bento/debian-10"
  config.vm.hostname = "deb4ccd"
  config.vm.provider "virtualbox" do |vb|
    vb.cpus = 1
    vb.memory = "2048"
    vb.name = "DebianMaker"
  end
  config.vm.provision "shell", inline: $script1
  config.vm.provision "shell", inline: $script2, privileged: false
  config.vm.provision "shell", inline: $script3
  config.vm.provision "shell", inline: $script4, privileged: false
end
