# Configure 2 so that 2 virtual machines are created. and note we need a new do block.
Vagrant.configure("2") do |config|

  config.vm.define "app" do |app|
  # configures the VM settings
    app.vm.box = "ubuntu/bionic64"
    app.vm.network "private_network", ip:"192.168.10.100"

  # Syncs the "app" folder to the "/home/vagrant/app" location on the VM, changes on either will affect the other.
    app.vm.synced_folder "app", "/home/vagrant/app"
  
  # provision the VM to have Nginx installed
    app.vm.provision "shell", path: "provision.sh", privileged: false
  end

  config.vm.define "db" do |db|

    db.vm.box = "ubuntu/bionic64"
    db.vm.network "private_network", ip:"192.168.10.150"

    db.vm.synced_folder "environment", "/home/vagrant/environment"

    app.vm.provision "shell", path: "provisiondb.sh", privileged: false

  end

end
