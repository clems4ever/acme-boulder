Vagrant.configure(2) do |config|

  config.vm.box = "debian/jessie64"
  config.vm.synced_folder ".", "/vagrant"
  ssh_pub_key = File.readlines("#{Dir.home}/.ssh/id_rsa.pub").first.strip
  config.vm.provision 'shell', inline: "echo #{ssh_pub_key} >> /home/vagrant/.ssh/authorized_keys", privileged: false
 

  config.vm.define "issuer" do |d|
    d.vm.network "private_network", ip: "192.168.2.100"
    d.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  end

  config.vm.define "boulder" do |d|
    d.vm.network "private_network", ip: "192.168.2.200"
    d.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
    end
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.sudo = true
    ansible.groups = {
      "boulders" => ["boulder"],
      "issuers" => ["issuer"]
    }
  end

end
