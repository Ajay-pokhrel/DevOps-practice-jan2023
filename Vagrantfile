Vagrant.configure(2) do |config|
    config.vm.define "controlnode" do |controlnode|
        controlnode.vm.box = "ubuntu/focal64"
        controlnode.vm.network "private_network", ip: "192.168.33.5"
        config.vm.synced_folder "../vagrant-jenkins-docker-ansible", "/complete-pipeline"
	controlnode.vm.provision :shell, path: "complete-pipeline/setup_scripts/ansiblesetup.sh"
        controlnode.vm.provision :shell, path: "complete-pipeline/setup_scripts/dockersetup.sh"
        controlnode.vm.provision :shell, path: "complete-pipeline/setup_scripts/jenkinssetup.sh"
    end
    config.vm.define "managednode" do |managednode|
        managednode.vm.box = "ubuntu/focal64"
        managednode.vm.network "public_network"
    end
end
