# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
  # Set box configuration
  config.vm.box = "precise32"
  config.vm.box_url = "http://files.vagrantup.com/precise32.box"

  # Assign this VM to a host-only network IP, allowing you to access it via the IP.
  config.vm.network :private_network, ip: "192.168.10.99"

  config.vm.synced_folder "../../waka/cosmeticanatural", "/srv/www/cosmeticanatural.dev", owner: "www-data", group: "www-data"

  # Enable provisioning with chef solo, specifying a cookbooks path (relative
  # to this Vagrantfile), and adding some recipes and/or roles.
  config.vm.provision :chef_solo do |chef|
    chef.cookbooks_path = "cookbooks"
    chef.data_bags_path = "data_bags"
    chef.add_recipe "vagrant_main"

    chef.json.merge!({
      "mysql" => {
        "server_root_password" => "magedev2013$",
        "server_repl_password" => "magedev2013$",
        "server_debian_password" => "magedev2013$"
      }
    })
  end
end
