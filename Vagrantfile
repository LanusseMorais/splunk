# -*- mode: ruby -*-
# vi: set ft=ruby  :

IMAGE_NAME = "almalinux/8"
SPLUNK_MEMORY=4096
SPLUNK_VCPU=4
NETWORK_PREFIX="192.168.165"
VM_GROUP_NAME="SPLUNK"
PASS_ADMIN="lanusse@123"

Vagrant.configure("2") do |config|

    #config.ssh.insert_key = false
    config.vm.define "splunk" do |splunk|
        splunk.vm.box = IMAGE_NAME
        splunk.vm.network "private_network", ip: "#{NETWORK_PREFIX}.30"
        splunk.vm.hostname = "splunk"
        splunk.vm.provider :virtualbox do |vb|
            vb.name = "splunk"
            vb.memory = SPLUNK_MEMORY
            vb.cpus = SPLUNK_VCPU
            vb.customize ["modifyvm", :id, "--groups", "/#{VM_GROUP_NAME}"]
        end        
        splunk.vm.provision "ansible" do |ansible|
            ansible.playbook = "splunk-setup/install-splunk.yml"
            ansible.groups = {
                "splunk_master" => ["splunk"]
            }
            ansible.extra_vars = {
                pass_admin: PASS_ADMIN
            }
        end
    end

end