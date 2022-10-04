Vagrant.require_version ">= 2.2.0"

Vagrant.configure(2) do |config|

  config.vm.box = "ubuntu/focal64"

  config.vm.synced_folder "synced_folder/", "/home/vagrant/synced_folder"

  # Forwards ports opened by the playgrounds to the host (the machine that runs vagrant)
  config.vm.network "forwarded_port", guest: 9090, host: 9090

  # Use ansible as for provisioning
  # https://www.vagrantup.com/docs/provisioning/ansible_local
  config.vm.provision "ansible_local" do |ansible|
    ansible.verbose = "v"
    ansible.playbook = "provision/playbook.yml"
    ansible.galaxy_roles_path = "/home/vagrant/roles"
    ansible.become = true
  end
end
