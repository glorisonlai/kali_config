Vagrant.configure("2") do |config|
  config.vm.box = "kalilinux/rolling"
  config.vm.define "kali"

  config.vm.network "public_network", "dev": "enp2s0", "mode": "bridge", "type": "bridge"

  config.vm.provider "libvirt" do |libvirt|
    libvirt.cpus = 1
    libvirt.memory = 4096
    libvirt.storage_pool_name="kali"
    libvirt.driver="kvm"
    libvirt.uri="qemu:///system"
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
    ansible.raw_arguments = Shellwords.shellsplit(ENV['ANSIBLE_ARGS']) if ENV['ANSIBLE_ARGS']
  end
end
