VAGRANTFILE_API_VERSION = "2"
Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  # All Vagrant configuration is done here.
  config.vm.box = 'precise64'
  config.vm.box_url = 'http://files.vagrantup.com/precise64.box'
  #config.vm.box_url = 'http://files.vagrantup.com/precise32.box'

  # synced (shared) folder with the host
  #config.vm.synced_folder ".", "/var/www/current", nfs: true, :exports_options => ['no_root_squash']
  #config.vm.synced_folder ".", "/var/www/current", :mount_options => ['m=777'], :nfs => true
  #config.vm.synced_folder ".", "/var/www/current"

  # in order to use NFS, we need host-only networking with a static ip address
  #config.vm.network :hostonly, "192.168.33.10"
  config.vm.network "private_network", ip: "192.168.33.12"
  config.vm.hostname = "fpm"

  # Create a forwarded port mapping which allows access to a specific port
  # within the machine from a port on the host machine. For this configuration
  # we will be accessing HTTP on port 4567.
  config.vm.network "forwarded_port", guest: 8080, host: 3000

  config.vm.provider "virtualbox" do |v|
    v.memory = 512
  end

  config.vm.provision "ansible" do |ansible|
    ansible.playbook = "deployment/provision.yml"
    ansible.inventory_path = "deployment/hosts"
  end

end