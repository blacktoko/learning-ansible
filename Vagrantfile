Vagrant.configure("2") do |config|

    config.vm.define "node1" do |node1|
        node1.vm.hostname = "node1.example.nl"
        node1.vm.box = "centos/7"
        node1.ssh.insert_key = false
        node1.vm.network :private_network, ip: "192.168.56.100"
        node1.vm.network "forwarded_port", guest: 22, host: 2210, id: "ssh"
    end

      #config.vm.define "node2" do |node2|
      #  node2.vm.hostname = "node2.example.nl"
      #  node2.vm.box = "centos/7"
      #  node2.ssh.insert_key = false
      #  node2.vm.network :private_network, ip: "192.168.56.101"
      #  node2.vm.network "forwarded_port", guest: 22, host: 2211, id: "ssh"
      #end

    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "playbooks/hello-world.yml"
        ansible.limit = "all"
    end

end