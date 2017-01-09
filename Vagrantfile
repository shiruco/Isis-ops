Vagrant.configure("2") do |config|
  config.vm.provider "virtualbox" do |v|
    v.memory = 1024
  end

  config.vm.define "isis-dev1" do |node|
    node.vm.box = "centos67"
    node.vm.box_url = "https://github.com/CommanderK5/packer-centos-template/releases/download/0.6.7/vagrant-centos-6.7.box"
    node.vm.network :private_network, ip: "192.168.33.10"
    node.vm.network :forwarded_port, guest: 3000, host: 3000
    node.ssh.insert_key = false
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "development.yml"
    ansible.inventory_path = "hosts"
    ansible.limit = 'all'
  end

end
