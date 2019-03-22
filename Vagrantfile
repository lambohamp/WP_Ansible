Vagrant.configure(2) do |config|
  config.vm.define "db" do |db|

    db.vm.box = "ubuntu/trusty64"

    db.vm.network "private_network", ip: "192.168.10.11"

    db.vm.hostname = "db"
  end

  config.vm.define "web" do |web|

    web.vm.box = "ubuntu/trusty64"

    web.vm.network "private_network", ip: "192.168.10.10"

    web.vm.hostname = "web"

    web.vm.network "forwarded_port", guest: 80, host: 80
  end

  config.vm.provision "ansible" do |ansible|
    ansible.verbose = ""
    ansible.playbook = "wp.yml"
    ansible.raw_arguments  = "--ask-vault-pass"
    end

end
