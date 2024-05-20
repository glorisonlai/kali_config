Vagrant.configure("2") do |config|
  config.vm.box = "kalilinux/rolling"
  config.vm.define "kalivBox"

  config.vm.provider "libvirt" do |libvirt|
    libvirt.cpus = 2
    libvirt.memory = 8192 
    libvirt.storage_pool_name="kali"
    libvirt.driver="kvm"
    libvirt.uri="qemu:///system"
  end

  config.vm.provider "virtualbox" do |vb|
    vb.gui = true
    vb.memory = 8192
    vb.cpus = 2
    vb.customize ["modifyvm", :id, "--cpuexecutioncap", "50"]
    vb.customize ["modifyvm", :id, "--clipboard", "bidirectional"]
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
    ansible.raw_arguments = Shellwords.shellsplit(ENV['ANSIBLE_ARGS']) if ENV['ANSIBLE_ARGS']
  end
end
