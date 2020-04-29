# -*- mode: ruby -*-
# vi: set ft=ruby :
Vagrant.configure('2') do |config|
  config.vm.box      = 'ubuntu/bionic64' # 18.04
  config.vm.hostname = 'activerecord-sqlserver-adapter-dev-box'

  config.vm.network :forwarded_port, guest: 3000, host: 3000
  config.vm.network :forwarded_port, guest: 1433, host: 1433

  config.vm.provision :shell, path: 'bootstrap.sh', keep_color: true
  config.vm.provision :shell, path: 'bootstrap_sqlserver.sh', keep_color: true

  config.vm.provider 'virtualbox' do |v|
    v.memory = ENV.fetch('ACTIVERECORD_SQLSERVER_DEV_BOX_RAM', 4098).to_i
    v.cpus   = ENV.fetch('ACTIVERECORD_SQLSERVER_DEV_BOX_CPUS', 2).to_i
  end
end
