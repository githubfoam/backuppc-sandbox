# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box_check_update = false

  # vbox template for all vagranth instances
  config.vm.provider "virtualbox" do |vb|
    vb.gui = false
    vb.memory = "512"
    vb.cpus = 2
  end

  # customize vagrant instance
  config.vm.define "lampstack-01" do |dockercluster|
    dockercluster.vm.box = "bento/ubuntu-19.04"
    dockercluster.vm.provider "virtualbox" do |vb|
      vb.name = "lampstack-01"
     end
     dockercluster.vm.network "private_network", ip: "192.168.1.120"
     dockercluster.vm.network "forwarded_port", guest: 80, host: 81
     dockercluster.vm.provision "ansible_local" do |ansible|
       ansible.playbook = "deploy.yml"
       ansible.become = true
       ansible.compatibility_mode = "2.0"
       ansible.version = "2.9.4"
     end
     dockercluster.vm.provision "shell", inline: <<-SHELL
     echo "===================================================================================="
                               hostnamectl status
     echo "===================================================================================="
     echo "         \   ^__^                                                                  "
     echo "          \  (oo)\_______                                                          "
     echo "             (__)\       )\/\                                                      "
     echo "                 ||----w |                                                         "
     echo "                 ||     ||                                                         "
     SHELL


  end

  # customize vagrant instance
  config.vm.define "lampstack-02" do |dockercluster|
    dockercluster.vm.box = "bento/centos-7.7"
    dockercluster.vm.network "private_network", ip: "192.168.1.121"
    dockercluster.vm.network "forwarded_port", guest: 80, host: 82
    dockercluster.vm.provider "virtualbox" do |vb|
      vb.name = "lampstack-02"
     end
     dockercluster.vm.provision "ansible_local" do |ansible|
       ansible.playbook = "deploy.yml"
       ansible.become = true
       ansible.compatibility_mode = "2.0"
       ansible.version = "2.9.3"
     end
    dockercluster.vm.provision "shell", inline: <<-SHELL
    echo "===================================================================================="
                              hostnamectl status
    echo "===================================================================================="
    echo "         \   ^__^                                                                  "
    echo "          \  (oo)\_______                                                          "
    echo "             (__)\       )\/\                                                      "
    echo "                 ||----w |                                                         "
    echo "                 ||     ||                                                         "
    SHELL
  end



end
