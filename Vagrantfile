# -*- mode: ruby -*-
# vi: set ft=ruby :

MACHINE_HOSTNAME='eeq.dev'
MACHINE_BOX='ubuntu/trusty64'
MACHINE_IP='192.168.11.20'
NFS_MOUNT_OPTIONS=['nolock,vers=3,udp,noatime,actimeo=1']

Vagrant.configure('2') do |config|
  config.vm.box = MACHINE_BOX
  config.vm.hostname = MACHINE_HOSTNAME

  config.ssh.shell = 'bash -c \'BASH_ENV=/etc/profile exec bash\''
  config.ssh.insert_key = false

  config.vm.network :private_network, ip: MACHINE_IP
  config.vm.network 'forwarded_port', guest: 80, host: 8080
  config.vm.synced_folder './', '/eeq', type: 'nfs', :mount_options => NFS_MOUNT_OPTIONS

  config.vm.provider 'virtualbox' do |vb|
    vb.customize ['modifyvm', :id, '--memory', 2048]
    vb.customize ['modifyvm', :id, '--cpus', 2]
  end

  config.vm.provision 'shell', inline: 'echo "cd /eeq" >> /home/vagrant/.bashrc'
end
