
Vagrant.configure("2") do |config|
  
  config.vm.define "server-db" do |dbserver|

    dbserver.vm.box = "ubuntu/trusty64"

    dbserver.vm.box_check_update = false

    #dbserver.vm.network "forwarded_port", guest: 8080, host: 8082

    dbserver.vm.network "private_network", type: "static", ip: "192.168.0.10"

    #dbserver.vm.synced_folder "./mysqldata", "/var/lib/mysql/"

    dbserver.vm.provider "virtualbox" do |vb|

      vb.gui = false
      vb.name = "server-mysql"
      vb.memory = "1024"
      vb.cpus = 1
    end
  end

  config.vm.define "preprodserver" do |preprodwebserver|

    preprodwebserver.vm.box = "bento/ubuntu-22.04"

    preprodwebserver.vm.box_check_update = false

    preprodwebserver.vm.network "forwarded_port", guest: 8080, host: 8083

    preprodwebserver.vm.network "private_network", type: "static", ip: "192.168.0.11"

    preprodwebserver.vm.synced_folder "./tomcatwebapps", "/opt/tomcat/webapps"

    preprodwebserver.vm.synced_folder "./tomcatconf", "/opt/tomcat/conf"

    preprodwebserver.vm.provider "virtualbox" do |vb|

      vb.gui = false
      vb.name = "preprodwebserver"
      vb.memory = "1024"
    end
  end
end
