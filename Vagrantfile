# -*- mode: ruby -*-
# vi: set ft=ruby :

# ATV 1 - VAGRANT
# Subir uma máquina virtual, usando Vagrant, com MySQL instalado e que esteja acessível no host da máquina na porta 3306.  

Vagrant.configure("2") do |config|

  #Utilizando o ubuntu
  config.vm.box = "ubuntu/bionic64"

  #Mapeando a porta 3306 (Utilizada por padrão em Myqsl)
  config.vm.network "forwarded_port", guest: 3306, host: 3306

  #Configurando uma virtualbox com 2 cpus e 1Gb de Ram 
  config.vm.provider "virtualbox" do |vb|
     vb.memory = "1024"
     vb.cpus = "2"
  end

  #Atualização o APT
  #Instalação do mysql 5.7
  #Alteração do arquivo de configuração mysqld.cnf
  # - bind-address = 0.0.0.0 (Libera acesso de outras maquinas ao mysql)
  config.vm.provision "shell", inline: <<-SHELL
     apt-get update
     apt-get install -y mysql-server-5.7
     cat /vagrant/mysql/mysqld.cnf > /etc/mysql/mysql.conf.d/mysqld.cnf
     service mysql restart
  SHELL

end