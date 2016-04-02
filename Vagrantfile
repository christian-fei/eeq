# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure('2') do |config|
  config.vm.box = 'ubuntu/trusty64'
  config.vm.hostname = 'eeq.dev'
  config.ssh.shell = 'bash -c \'BASH_ENV=/etc/profile exec bash\''

  config.vm.provider "virtualbox" do |vb|
    vb.customize ["modifyvm", :id, "--memory", 2048]
    vb.customize ["modifyvm", :id, "--cpus", 2]
  end

  config.vm.network :private_network, ip: "192.168.11.20"
  config.vm.network "forwarded_port", guest: 80, host: 8080

  config.vm.synced_folder "./", "/eeq", type: "nfs", :mount_options => ['nolock,vers=3,udp,noatime,actimeo=1']

  config.vm.provision "shell",
    inline: "echo 'cd /eeq' >> /home/vagrant/.bashrc"
end