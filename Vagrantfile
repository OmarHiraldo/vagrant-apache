Vagrant.configure("2") do |config|
    # Configuración básica para la máquina virtual
    config.vm.box = "ubuntu/bionic64"  # Usaremos una imagen de Ubuntu
  
    # Red privada con una IP estática
    config.vm.network "private_network", type: "static", ip: "192.168.56.10"  # Asignamos una IP estática a la VM
  
    # Asignación de recursos a la VM
    config.vm.provider "virtualbox" do |vb|
      vb.memory = "512"  # 512 MB de RAM
      vb.cpus = 1        # 1 CPU
    end
  
    # Nombre de la máquina
    config.vm.hostname = "apache-server"
  
    # Directorio compartido entre el host y la VM
    config.vm.synced_folder ".", "/var/www/html", type: "virtualbox", SharedFoldersEnableSymlinksCreate: false
  
    # Provisión para instalar Apache
    config.vm.provision "shell", inline: <<-SHELL
      sudo apt-get update
      sudo apt-get install -y apache2  # Instalación de Apache
      sudo systemctl enable apache2    # Habilitar Apache para iniciar en el arranque
      sudo systemctl start apache2     # Iniciar Apache
    SHELL
  end
  