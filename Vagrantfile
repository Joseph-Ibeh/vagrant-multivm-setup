Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/focal64" 

  config.vm.define "web01" do |web01|
    web01.vm.hostname = "web01"
    web01.vm.network "private_network", ip: "192.168.56.41"
    web01.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  end

  config.vm.define "web02" do |web02|
    web02.vm.hostname = "web02"
    web02.vm.network "private_network", ip: "192.168.56.42"
    web02.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end
  end

  config.vm.define "db01" do |db01|
    db01.vm.hostname = "db01"
    db01.vm.network "private_network", ip: "192.168.56.43"
    db01.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 2
    end
    db01.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update -y
      sudo apt-get install -y wget unzip mysql-server -y
      sudo systemctl enable mysql
      sudo systemctl start mysql
      echo "Database server setup completed."
    SHELL
  end
end
