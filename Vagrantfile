# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  config.vm.box = "precise64"
  config.vm.box_url = "http://files.vagrantup.com/precise64.box"
  config.vm.network :private_network, ip: "192.168.33.13"

  # config.vm.network :public_network

  # Share an additional folder to the guest VM. The first argument is
  # the path on the host to the actual folder. The second argument is
  # the path on the guest to mount the folder. And the optional third
  # argument is a set of non-required options.
  # config.vm.synced_folder "../collectd-web", "/collectd-web"

  config.vm.provider :virtualbox do |vb|
    vb.customize ["modifyvm", :id, "--memory", "128"]
  end

  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.add_recipe('collectd::server')
    chef.add_recipe('collectd::collectd_web_apache')
    #chef.add_recipe('collectd::client')
    # You may also specify custom JSON attributes:
    # chef.json = {
    #   :collectd => {
    #     :collectd_web => {
    #       :path => '/collectd-web'
    #     }
    #   }
    # }
  end
end
