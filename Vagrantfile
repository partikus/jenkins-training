# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|

    config.vm.box = "ubuntu/trusty64"
    config.vm.network "private_network", ip: "10.0.0.200"
    config.ssh.forward_agent = true
    config.vm.synced_folder "./src/", "/var/www/", id: "vagrant-root", type: "nfs"
    
    config.vm.provider "virtualbox" do |vb|
        vb.gui = false
        vb.memory = "2048"
        vb.cpus = 2
        vb.customize ["modifyvm", :id, "--name", "jenkins-default"]
    end

    config.vm.provision "shell",
        inline: "
          sudo apt-get --yes install software-properties-common;
          sudo apt-get --yes install python-pip;
          if ! type ansible-playbook; then
              sudo apt-add-repository --yes ppa:ansible/ansible;
              sudo apt-get --yes update
              sudo apt-get --yes install ansible
          fi
          id -u
          cp -R /vagrant ~/;
          chmod -x ~/vagrant/hosts;
          chmod -x ~/vagrant/provision.yml;
          cd ~/vagrant;
          ansible-playbook -i hosts provision.yml;
      "
end
