
Vagrant.configure("2") do |config|

  config.vm.box = "bento/ubuntu-24.04"

  config.vm.hostname = "webserver"

  config.vm.network "forwarded_port",
    guest: 80,
    host: 8080

  config.vm.provider "vmware_desktop" do |vm|
    vm.vmx["memsize"] = "2048"
    vm.vmx["numvcpus"] = "2"
  end

end
