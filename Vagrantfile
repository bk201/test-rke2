
$script0 = <<-SCRIPT0

curl -sfL https://get.rke2.io | INSTALL_RKE2_VERSION=v1.21.3+rke2r1 sh -
systemctl enable --now rke2-server

SCRIPT0

Vagrant.configure("2") do |config|
  config.vm.box = "opensuse/Leap-15.3.x86_64"
#  config.vm.box = "generic/ubuntu2004"
  config.vm.define "node1" do |node|
    node.vm.hostname = "node1"
    node.vm.provider "libvirt" do |lv|
      lv.cpu_mode = 'host-passthrough'
      lv.memory = 4096
      lv.cpus = 4
    end
  end

  config.vm.provision "shell", inline: $script0
end


