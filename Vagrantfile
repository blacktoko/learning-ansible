Vagrant.configure("2") do |config|
  servers=[
    {
      :hostname => "controller",
      :box => "centos/7",
      :ip => "192.168.56.100",
      :ssh_port => '2210',
    },
    {
      :hostname => "node1",
      :box => "centos/7",
      :ip => "192.168.56.101",
      :ssh_port => '2211',
    }

  ]

  servers.each do |machine|

    config.vm.define machine[:hostname] do |node|
      #node.ssh.insert_key = false
      node.vm.box = machine[:box]
      node.vm.hostname = machine[:hostname]

      node.vm.network :private_network, ip: machine[:ip]
      node.vm.network "forwarded_port", guest: 22, host: machine[:ssh_port], id: "ssh"

      node.vm.provision "file", source: "authorized_keys", destination: "/home/vagrant/.ssh/authorized_keys"

      node.vm.provision "shell",
        inline: "chmod 600 /home/vagrant/.ssh/authorized_keys"



      node.vm.provider :virtualbox do |v|
        v.customize ["modifyvm", :id, "--memory", 512]
        v.customize ["modifyvm", :id, "--name", machine[:hostname]]
      end
    end

    config.vm.provision "ansible_local" do |ansible|
        ansible.playbook = "playbooks/hello-world.yml"
    end

  end
end