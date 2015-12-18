# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
    config.vm.define "default", primary: true do |v|
        
        v.vm.box = "ubuntu/trusty64"
        v.vm.network "private_network", ip: "10.0.0.200"
        v.ssh.forward_agent = true
        
        v.vm.provider "virtualbox" do |vb|
            vb.gui = false
            vb.memory = "2048"
            vb.cpus = 2
            vb.customize ["modifyvm", :id, "--name", "jenkins-default"]
        end

        v.vm.provision "ansible" do |ansible|
            ansible.playbook = "jenkins.yml"
            ansible.inventory_path = "hosts"
            ansible.limit = "jenkins"
            ansible.verbose = "vv"
        end
    end

    config.vm.define "docker", autostart: false do |v|
        
        v.vm.box = "ubuntu/trusty64"
        v.vm.network "private_network", ip: "10.0.0.201"
        v.ssh.forward_agent = true
        
        v.vm.provider "virtualbox" do |vb|
            vb.gui = false
            vb.memory = "4096"
            vb.cpus = 2
            vb.customize ["modifyvm", :id, "--name", "jenkins-dockernode"]
        end

        v.vm.provision "ansible" do |ansible|
            ansible.playbook = "docker.yml"
            ansible.inventory_path = "hosts"
            ansible.limit = "nodes"
        end
    end
end
