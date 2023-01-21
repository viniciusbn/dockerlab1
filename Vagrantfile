Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64"
  config.vm.provider "virtualbox" do |virtualbox|
    virtualbox.memory = 512
    virtualbox.cpus = 1
  end

  config.vm.define "docker" do |docker|
    docker.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "docker"
    end
    docker.vm.network "private_network", ip: "192.168.20.10"
    #Install Docker
    docker.vm.provision "shell", inline: "curl -fsSL https://get.docker.com -o get-docker.sh && sh get-docker.sh"
    #Set ssh keys
    docker.vm.provision "shell", inline: "cat /vagrant/configs/ssl/id_bionic.pub >> .ssh/authorized_keys"
  end

end