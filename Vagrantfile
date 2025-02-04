
Vagrant.configure("2") do |config|
  config.vm.box = "generic/debian12"

  # Configuração do provider VirtualBox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"

    # Criar e anexar 3 discos de 10GB
    ["diskp", "disks", "diskt"].each_with_index do |disk, index|
      vb.customize ["createhd", "--filename", disk, "--size", 10240] # 10 GB

      vb.customize [
        "storageattach", :id,
        "--storagectl", "SATA Controller",
        "--port", index + 1, "--device", 0,
        "--type", "hdd",
        "--medium", "#{disk}.vdi"
      ]
    end
  end

  config.vm.network "private_network", ip: "192.168.57.10"
  config.vm.hostname = "HelioJessica"

  # Configuração de provisionamento Ansible
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "playbook.yml"
    ansible.compatibility_mode = "2.0"
  end
end
