Vagrant.configure("2") do |config|
  config.vm.box = "kalilinux/rolling"
  config.vm.define "kali"

  config.vm.provider "libvert" do |lb|
    lb.cpus = 1
    lb.memory = 4096
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "playbook.yml"
  end
end
