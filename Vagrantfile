# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure(2) do |config|
  config.vm.box = 'ubuntu/trusty64'
  config.vm.hostname = 'ruby-dev'

  if Vagrant.has_plugin? 'vachant-cachier'
    config.cache.scope = :box
    config.cache.auto_detect = false
    config.cache.enable :apt
    config.cache.enable :apt_lists
    config.cache.enable :gem
  end

  config.vm.network 'forwarded_port', guest: 3306, host: 3306

  config.vm.provision 'shell', path: 'provisioning/install-rvm.sh', \
    args: 'stable'

  config.vm.provision 'shell', path: 'provisioning/install-ruby.sh', \
    args: '2.2.2'

  config.vm.provision 'shell', path: 'provisioning/install-mysql.sh', \
    args: 'mysql-password'
end
