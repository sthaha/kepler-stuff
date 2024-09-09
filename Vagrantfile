Vagrant.configure("2") do |config|
  config.vm.box = "fedora/40-cloud-base"
  config.vm.box_version = "40.20240414.0"
  # config.vm.network "public_network", ip: "192.168.111.222", dev: "virbr0"
  #
  # config.vm.network :private_network, ip: "192.168.111.222"


  config.vm.provider :libvirt do |virt|
    virt.driver = "kvm"
    virt.memory = 2048
    virt.cpus = 2
    virt.cpuaffinitiy 0 => '0', 1 => '1'
  end

  config.vm.hostname = "vm.kepler.dev"

  config.vm.synced_folder "./vm/dev", "/vagrant",
    type: "rsync",
    rsync__auto: true


  # config.vm.provision "shell", path: "provision.sh"
  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "ansible/playbook.yml"
    ansible.verbose = "vv"
  end


end

# commands
# vagrant ssh-config
