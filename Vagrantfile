VAGRANTFILE_API_VERSION = "2"

#service_name = 'doc-reg'

Vagrant.configure(VAGRANTFILE_API_VERSION)  do |config|
  config.vm.box = "ubuntu/vivid"
  config.vm.hostname = "doc-reg"

  config.vm.network :forwarded_port, guest: 80, host: 8080
  config.vm.network :forwarded_port, guest: 443, host: 8443

  config.vm.provider "virtualbox" do |v|
    v.cpus = 1
    v.memory = 1024
  end

  config.vm.provision :ansible do |ansible|
    ansible.inventory_path = "vagrant-inv.ini"
    ansible.playbook = "vagrant-play.yml"
    ansible.extra_vars = { user: "vagrant" }
    ansible.sudo = true
  end
end
