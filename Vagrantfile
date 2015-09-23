# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  # The most common configuration options are documented and commented below.
  # For a complete reference, please see the online documentation at
  # https://docs.vagrantup.com.

  # Every Vagrant development environment requires a box. You can search for
  # boxes at https://atlas.hashicorp.com/search.
  config.vm.box = "ubuntu/trusty64"

   config.vm.network :public_network, ip: "192.168.100.250"
  config.vm.network :private_network, ip: "33.33.33.33"


  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "1024"]
  end
  
  config.vm.synced_folder "../vagrant-lamp-phpmyadmin/laravel", "/vagrant_data"

  

  # Define a Vagrant Push strategy for pushing to Atlas. Other push strategies
  # such as FTP and Heroku are also available. See the documentation at
  # https://docs.vagrantup.com/v2/push/atlas.html for more information.
  # config.push.define "atlas" do |push|
  #   push.app = "YOUR_ATLAS_USERNAME/YOUR_APPLICATION_NAME"
  # end

  # Enable provisioning with a shell script. Additional provisioners such as
  # Puppet, Chef, Ansible, Salt, and Docker are also available. Please see the
  # documentation for more information about their specific syntax and use.
  config.vm.provision "shell", inline: <<-SHELL
    sudo apt-get update
    sudo apt-get install -y git
    sudo apt-get install -y build-essential
    sudo apt-get install -y vim
    sudo apt-get install -y php5 php5-mysql 
    sudo apt-get install -y apache2
    sudo apt-get install -y mysql-server-5.6
    sudo apt-get install -y phpmyadmin
      sudo a2ensite default
      sudo ln -s /etc/phpmyadmin/apache.conf /etc/apache2/conf-available/phpmyadmin.conf
      sudo a2enconf phpmyadmin
      sudo /etc/init.d/apache2 reload
    curl -s https://getcomposer.org/installer | php
    sudo mv composer.phar /usr/local/bin/composer  

  SHELL
end
