NODE_COUNT = 2

Vagrant.configure("2") do |config|
  (1..NODE_COUNT).each do |i|
    config.vm.define "vm#{i}" do |subcfg|
      subcfg.vm.hostname = "vm#{i}"
      subcfg.vm.box = "hashicorp/bionic64"
      subcfg.vm.box_version = "1.0.282"
      subcfg.vm.network :private_network, ip: "192.168.50.#{i*10}"
      subcfg.ssh.username = 'vagrant'
      subcfg.ssh.password = 'vagrant'
      subcfg.ssh.insert_key = false
      subcfg.vm.provision "shell", inline: <<-SHELL
        sudo apt-get update
        sudo apt-get install -y git
        git config --global user.name "szanko02"
        git config --global user.email "stas.060232@gmail.com"
        git clone -b Module-2 https://github.com/szanko02/vagrant
        cat vagrant/README.md
      SHELL
    end  
  end
end
