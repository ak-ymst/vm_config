# coding: utf-8

Vagrant.configure("2") do |config|
    config.vm.provider :virtualbox do |v|
        v.name = "centos7.1"
        v.customize ["modifyvm", :id, "--memory", 1024]
    end

    config.vm.box = "centos7.1"
    config.vm.box_url = "https://github.com/CommanderK5/packer-centos-template/releases/download/0.7.1/vagrant-centos-7.1.box"
    config.vm.hostname = "vagrant-centos7.1"

    config.vm.network :private_network, ip: "192.168.56.100"
    config.ssh.forward_agent = true

    config.vm.synced_folder "share/", "/vagrant"

    # Ansible provisioning
    config.vm.provision "ansible" do |ansible|
        ansible.playbook = "ansible/playbook.yml"
        ansible.inventory_path = "ansible/hosts"
        ansible.limit = 'all'
    end
end
