Vagrant.configure("2") do |config|
  boxes = [
    { :name => "node1", :box => "centos/7" }
  ]
  boxes.each do |opts|
    config.vm.define opts[:name] do |config|
      config.vm.box = opts[:box]
      if opts[:name] == boxes.last[:name]
        config.vm.provision "ansible" do |ansible|
          ansible.playbook = "playbooks/test.yml"
          ansible.limit = "all"
        end
      end
    end
  end
end