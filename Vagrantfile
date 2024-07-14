Vagrant.configure("2") do |config|
  config.vm.box = "ubuntu/jammy64"

  # Compartir la carpeta actual con las máquinas virtuales
  config.vm.synced_folder ".", "/vagrant"

  # Servidor 1
  config.vm.define "web1" do |web1|
    web1.vm.hostname = "web1"
    web1.vm.network "forwarded_port", guest: 80, host: 8080

    web1.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end

    web1.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      cp /vagrant/index.html /var/www/html/index.html
    SHELL
  end

  # Servidor 2
  config.vm.define "web2" do |web2|
    web2.vm.hostname = "web2"
    web2.vm.network "forwarded_port", guest: 80, host: 8081

    web2.vm.provider "virtualbox" do |vb|
      vb.memory = "512"
      vb.cpus = 1
    end

    web2.vm.provision "shell", inline: <<-SHELL
      apt-get update
      apt-get install -y apache2
      cp /vagrant/index.html /var/www/html/index.html
    SHELL
  end
end