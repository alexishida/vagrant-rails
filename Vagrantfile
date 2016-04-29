# -*- mode: ruby -*-
# vi: set ft=ruby :

$script = <<SCRIPT
echo Provisionando...
date > /etc/vagrant_provisioned_at
SCRIPT

Vagrant.configure("2") do |config|

  # Allow symbolic links into shared folder ( Execute terminal as the system administrator ) only Windows
  # config.vm.provider "virtualbox" do |v|
  #  v.customize ["setextradata", :id, "VBoxInternal2/SharedFoldersEnableSymlinksCreate/v-root", "1"]
  # end


  config.vm.box_url = "https://s3.alexishida.com/vagrant/20160428-ubuntu1404-rails-pg.box"
  config.vm.box = "20160428-ubuntu1404-rails-pg"


  config.vm.host_name = "mybox"
  config.vm.provision "shell", inline: $script

  # Windows
  #config.vm.synced_folder "C:/desenvolvimento", "/home/vagrant/desenvolvimento"

  #Linux
  config.vm.synced_folder "/home/alexishida/desenvolvimento", "/home/vagrant/desenvolvimento"

  #config.ssh.insert_key = false

  config.vm.provider "virtualbox" do |vb|
     vb.memory = 2048
     vb.cpus = 2
  end

  # Port forwarding
  config.vm.network "forwarded_port", guest: 8181, host: 8181 # Rails Server
  config.vm.network "forwarded_port", guest: 3000, host: 3000 # Rails Server
  config.vm.network "forwarded_port", guest: 5432, host: 5432 # Postgres
  config.vm.network "forwarded_port", guest: 15432, host: 15432  # Postgres
end
