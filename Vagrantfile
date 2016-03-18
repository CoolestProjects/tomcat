# -*- mode: ruby -*-
# vi: set ft=ruby :

Vagrant.configure("2") do |config|
 
  config.vm.hostname = "vs-tomcat-berkshelf"

  config.vm.box_url = "file:////Users/noelking/development/opscode_centos-6.4_chef-11.4.4.box"
  config.vm.box = "platform-centos"
  config.vm.network :private_network, ip: "33.33.33.10"

  config.vm.network :forwarded_port, guest: 8080, host: 8888  # Web ap
 config.berkshelf.enabled = true

  config.vm.provision :chef_solo do |chef|

    chef.log_level = :debug

    chef.json = {
      :java => {
        :oracle => {
        "accept_oracle_download_terms" => true
       },
       :oracle_rpm => {
        "type" => "jdk"
       }, 
       "jdk_version" => '7',
       "install_flavor" => 'oracle'
      }
    }

    chef.run_list = [
        "recipe[java::default]",
        "recipe[tomcat::default]"
    ]
  end
end

