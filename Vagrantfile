# -*- mode: ruby -*-
# vi: set ft=ruby :

VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |configure|

  configure.vm.define :docker_nodemcu do |config|
    config.vm.box = "ubuntu/vivid64"
    config.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/vivid/current/vivid-server-cloudimg-amd64-vagrant-disk1.box"
    config.vm.box_download_checksum = "aa4909d366484f511e019505acc30504"
    config.vm.box_download_checksum_type = "md5"
    config.vm.network :private_network, ip: "10.20.20.20"
    config.vm.network :forwarded_port, guest: 80, host: 8000
    config.vm.network :forwarded_port, guest: 8080, host: 8080
    config.vm.network :forwarded_port, guest: 8081, host: 8081

    config.vm.provider "virtualbox" do |v|
      v.memory = 2048
      v.cpus = 2
    end

    config.vm.provision "docker" do |d|
      d.pull_images "ubuntu"
    end

    config.vm.synced_folder "/Users/mdesilva/internal/iot/", "/iot/"
  end
end
