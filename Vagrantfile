# -*- mode: ruby -*-
# vi: set ft=ruby :

# Vagrantfile API/syntax version. Don't touch unless you know what you're doing!
VAGRANTFILE_API_VERSION = "2"

$script = <<SCRIPT
export HUGO=hugo_0.12_linux_amd64

wget -q https://github.com/spf13/hugo/releases/download/v0.12/${HUGO}.tar.gz -O /tmp/${HUGO}.tar.gz
sudo mkdir /opt/hugo
sudo tar xvzf /tmp/${HUGO}.tar.gz -C /opt/hugo

sudo ln -s /opt/hugo/${HUGO}/${HUGO} /usr/local/bin/hugo
SCRIPT

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "ubuntu/trusty64"

  # Forward hugo server port
  config.vm.network "forwarded_port", guest: 1313, host: 1313

  config.vm.provision "shell", inline: $script
end
