Vagrant.configure("2") do |config|
  config.vm.box = "hashicorp/bionic64"
  config.vm.box_version = "1.0.282"

  config.vm.define "master" do |k8s|
    k8s.vm.hostname = "k8s-master"
    k8s.vm.box_check_update = false
    k8s.vm.network "public_network", ip: "192.168.101.10"
    k8s.vm.network "private_network", ip: "10.1.1.10"
    if Vagrant.has_plugin?("vagrant-timezone")
      k8s.timezone.value = "Europe/Minsk"
    end
    k8s.vm.provider "virtualbox" do |v|
      v.memory = 4096
      v.cpus = 2
      v.name = "k8s-master"
    end
    k8s.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "master-playbook.yml"
    end
  end

  config.vm.define "node1" do |worker1|
    worker1.vm.hostname = "k8s-node1"
    worker1.vm.box_check_update = false
    worker1.vm.network "public_network", ip: "192.168.101.20"
    worker1.vm.network "private_network", ip: "10.1.1.20"
    if Vagrant.has_plugin?("vagrant-timezone")
      worker1.timezone.value = "Europe/Minsk"
    end  
    worker1.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 2
      vb.name = "k8s-node1"
    end
    worker1.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "node1-playbook.yml"
    end
  end

  config.vm.define "node2" do |worker2|
    worker2.vm.hostname = "k8s-node2"
    worker2.vm.box_check_update = false
    worker2.vm.network "public_network", ip: "192.168.101.30"
    worker2.vm.network "private_network", ip: "10.1.1.30"
    if Vagrant.has_plugin?("vagrant-timezone")
      worker2.timezone.value = "Europe/Minsk"
    end  
    worker2.vm.provider "virtualbox" do |vb|
      vb.memory = 1024
      vb.cpus = 2
      vb.name = "k8s-node2"
    end
    worker2.vm.provision "ansible_local" do |ansible|
      ansible.playbook = "node2-playbook.yml"
    end
  end
end
