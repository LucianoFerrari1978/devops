Vagrant.configure("2") do |config|

  config.vm.provision "shell", path: "script.sh"

    config.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "playbook.yml"
      ansible.install_mode = "pip"
    end

  config.vm.define "controle" do |controle|
    controle.vm.box = "shekeriev/debian-11"
    controle.vm.hostname = "controle"
#    controle.vm.network "private_network", ip: "172.17.177.100", virtualbox__intnet: "mynetwork"
    controle.vm.network "private_network", ip: "172.17.177.100", name: "vboxnet1"
    controle.vm.provider "vitualbox" do |vb|
      vb.name = "controle"
      vb.memory = "2048"
      vb.cpus = 2
      vb.gui = true
    end
  end
  
  config.vm.define "web" do |web|
    web.vm.box = "shekeriev/debian-11"
    web.vm.hostname = "web"
#    web.vm.network "private_network", ip: "172.17.177.101", virtualbox__intnet: "mynetwork"
    web.vm.network "private_network", ip: "172.17.177.101", name: "vboxnet1"
    web.vm.provider "vitualbox" do |vb|
      vb.name = "web"
      vb.memory = "512"
      vb.cpus = 2
      vb.gui = true
    end
  end


  config.vm.define "db" do |db|
    db.vm.box = "shekeriev/debian-11"
    db.vm.hostname = "db"
#    db.vm.network "private_network", ip: "172.17.177.102", virtualbox__intnet: "mynetwork"
    db.vm.network "private_network", ip: "172.17.177.102", name: "vboxnet1"
    db.vm.provider "vitualbox" do |vb|
      vb.name = "db"
      vb.memory = "512"
      vb.cpus = 2
      vb.gui = true
    end
  end


  config.vm.define "puppet" do |puppet|
    puppet.vm.box = "shekeriev/debian-11"
    puppet.vm.hostname = "puppet"
#    puppet.vm.network "private_network", ip: "172.17.177.102", virtualbox__intnet: "mynetwork"
    puppet.vm.network "private_network", ip: "172.17.177.200", name: "vboxnet1"
    puppet.vm.provider "vitualbox" do |vb|
      vb.name = "puppet"
      vb.memory = "4096"
      vb.cpus = 2
      vb.gui = true
    end
    puppet.vm.provision "shell", inline: "echo 'nameserver 1.1.1.1' > /etc/resolv.conf"
  end

end
