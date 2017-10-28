# -*- mode: ruby -*-
# vi: set ft=ruby :

ENV['VAGRANT_DEFAULT_PROVIDER'] = 'libvirt'
Vagrant.configure(2) do |cnfg|
  cnfg.vm.define 'minishift-vm' do |mvm|
    mvm.vm.box = 'centos/7'
    mvm.vm.box_url = mvm.vm.box
    mvm.vm.provider 'libvirt' do |prv|
      prv.nested = true
      prv.memory = 4096
      prv.cpus = 2
    end
    mvm.vm.provision :shell, :inline => "yum -y install wget git"
    mvm.vm.provision :shell, :inline => "wget https://github.com/minishift/minishift/releases/download/v1.7.0/minishift-1.7.0-linux-amd64.tgz"
    mvm.vm.provision :shell, :inline => "tar -zxf minishift-1.7.0-linux-amd64.tgz"
    mvm.vm.provision :shell, :inline => "echo 'export PATH=$PATH:$HOME/minishift-1.7.0-linux-amd64' >>$HOME/.bashrc"
    mvm.vm.provision :shell, :inline => "source $HOME/.bashrc"
  end
end
