Vagrant.configure("2") do |config|

  # SSH Settings
  config.ssh.insert_key = false
  config.ssh.private_key_path = ["./keys/ansible.key", "~/.vagrant.d/insecure_private_key"]

  # Add public key
  config.vm.provision "shell" do |key|
    ssh_pub_key = File.readlines("keys/ansible.key.pub").first.strip
    key.inline = <<-SHELL
      mkdir -p /home/vagrant/.ssh/
      touch /home/vagrant/.ssh/authorized_keys
      echo #{ssh_pub_key} > /home/vagrant/.ssh/authorized_keys
      chown -R vagrant:vagrant /home/vagrant
      exit 0
    SHELL
  end

#
#------------------ ubuntu 22.04 ------------------------------------------
  config.vm.define "ubuntu" do |ubuntu|
    ubuntu.vm.box = "ubuntu/jammy64"
    ubuntu.vm.hostname = "ubuntu"

    ubuntu.vm.synced_folder ".", "/vagrant", disabled: true

    ubuntu.vm.network "forwarded_port",
      guest: 80,
      host: 8081,
      host_ip: "127.0.0.1"

   ubuntu.vm.network "forwarded_port",
      guest: 443,
      host: 4341,
      host_ip: "127.0.0.1"

    ubuntu.vm.network "forwarded_port",
      guest: 22,
      host: 2321,
      host_ip: "127.0.0.1"

    ubuntu.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "ubuntu"
      virtualbox.memory = "2048"
      virtualbox.cpus = 6

      virtualbox.default_nic_type = "82543GC"
    end # end provider

     ubuntu.vm.provision "shell", inline: <<-SHELL
       echo "all is good"
     SHELL

  end # end define
#----------------------------------------------------------------------------
#
#------------------ debiab11 ------------------------------------------
  config.vm.define "debian" do |debian|
    debian.vm.box = "debian/bullseye64"
    debian.vm.hostname = "debian"

    debian.vm.synced_folder ".", "/vagrant", disabled: true

    debian.vm.network "forwarded_port",
      guest: 80,
      host: 8082,
      host_ip: "127.0.0.1"

    debian.vm.network "forwarded_port",
      guest: 443,
      host: 4342,
      host_ip: "127.0.0.1"

    debian.vm.network "forwarded_port",
      guest: 22,
      host: 2322,
      host_ip: "127.0.0.1"

    debian.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "debian"
      virtualbox.memory = "2048"
      virtualbox.cpus = 6

      virtualbox.default_nic_type = "82543GC"
    end # end provider

     debian.vm.provision "shell", inline: <<-SHELL
       echo "all is good"
     SHELL

  end # end define
#------------------------------------------------------------

  config.vm.define "rocky" do |rocky|
    rocky.vm.box = "rockylinux/8"
    rocky.vm.hostname = "rocky"

    rocky.vm.synced_folder ".", "/vagrant", disabled: true

    rocky.vm.network "forwarded_port",
      guest: 80,
      host: 8083,
      host_ip: "127.0.0.1"

    rocky.vm.network "forwarded_port",
      guest: 443,
      host: 4343,
      host_ip: "127.0.0.1"

    rocky.vm.network "forwarded_port",
      guest: 22,
      host: 2323,
      host_ip: "127.0.0.1"

    rocky.vm.provider "virtualbox" do |virtualbox|
      virtualbox.name = "rocky"
      virtualbox.memory = "2048"
      virtualbox.cpus = 6

      virtualbox.default_nic_type = "82543GC"
    end # end provider

     rocky.vm.provision "shell", inline: <<-SHELL
       echo "all is good"
     SHELL

  end # end define

end
