Vagrant.configure(2) do |config|
  config.vm.box = "CentOS64"
  config.vm.box_url = "https://github.com/2creatives/vagrant-centos/releases/download/v6.5.3/centos65-x86_64-20140116.box"

  config.vm.network "private_network", ip: "192.168.33.30"
  config.vm.synced_folder "../dev", "/home/vagrant/dev", create: true, owner: "vagrant", group: "vagrant"

  config.vm.provider "virtualbox" do |vb|
    vb.memory = "1024"
  end

  config.vm.provision "chef_zero" do |chef|
    chef.version = '11.18.0'
    chef.cookbooks_path = ["./cookbooks", "./berks-cookbooks"]
    chef.add_recipe "vim"
    chef.add_recipe "yum"
    chef.add_recipe "ruby_build"
    chef.add_recipe "rails_support"
    chef.add_recipe "rbenv::user"
    chef.json = {
      "rbenv" => {
        "user_installs" => [{
          "user" => "vagrant",
          "rubies" => ["2.1.5"],
          "global" => "2.1.5",
          "gems" => { "2.1.5" => [{"name" => "bundler"}] }
        }]
      }
    }
  end
end
