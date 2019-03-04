# -*- mode: ruby -*-
# vi: set ft=ruby :

boxes=[
  {
    :name => "mariadb",
    :host => "192.168.56.102"
  }
]

Vagrant.configure("2") do |config|
  boxes.each do |box|
    config.vm.define box[:name] do |node|
      node.vm.box = "ubuntu/bionic64"
      node.vm.hostname = box[:name]
      node.vm.box_url = "ubuntu/bionic64"
    
      node.vm.network :private_network, ip: box[:host]
    
      node.vm.provider :virtualbox do |v|
        v.customize ["modifyvm", :id, "--natdnshostresolver1", "on"]
        v.customize ["modifyvm", :id, "--memory", 512]
        v.customize ["modifyvm", :id, "--name", box[:name]]
      end

      node.ssh.insert_key = false
      node.ssh.private_key_path = ['~/.vagrant.d/insecure_private_key', '~/.ssh/id_rsa']
      node.vm.provision "file", source: "~/.ssh/id_rsa.pub", destination: "~/.ssh/authorized_keys"
      node.ssh.forward_agent = true

      node.vm.provision :shell, inline: "apt install python -y"
    end
  end
end
