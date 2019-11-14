Vagrant.configure("2") do |config|
	# CONFIGURACION GENERAL.
	config.vm.box = "centos/7"

        # VM - ELASTIC SEARCH
        config.vm.define "elastic" do |elastic|
                elastic.vm.hostname = "elastic1.everis.com"
                elastic.vm.network "public_network", ip: "192.168.1.201"
                elastic.vm.provider "virtualbox" do |elastic_vb|
                        elastic_vb.memory = "2048"
                        unless File.exist?('.vagrant/machines/elastic/secondDisk.vdi')
                        elastic_vb.customize ['createhd', '--filename', '.vagrant/machines/elastic/secondDisk.vdi', '--variant', 'Standard', '--size', 10 * 1024]
                        end
                        elastic_vb.customize ['storageattach', :id,  '--storagectl', 'IDE', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', '.vagrant/machines/elastic/secondDisk.vdi']
                end
        end

	# VM - KIBANA
	config.vm.define "kibana" do |kibana|
        	kibana.vm.network "public_network", ip: "192.168.1.200"
                kibana.vm.hostname = "kibana.everis.com"
		kibana.vm.provider "virtualbox" do |kibana_vb|
			kibana_vb.memory = "2048"
			unless File.exist?('.vagrant/machines/kibana/secondDisk.vdi')
			kibana_vb.customize ['createhd', '--filename', '.vagrant/machines/kibana/secondDisk.vdi', '--variant', 'Standard', '--size', 10 * 1024]
			end
			kibana_vb.customize ['storageattach', :id,  '--storagectl', 'IDE', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', '.vagrant/machines/kibana/secondDisk.vdi']
		end
	end

	# VM - LOGSTASH
	config.vm.define "logstash" do |logstash|
		logstash.vm.hostname = "logstash.everis.com"
        	logstash.vm.network "public_network", ip: "192.168.1.202"
		logstash.vm.provider "virtualbox" do |logstash_vb|
			logstash_vb.memory = "2048"		
			unless File.exist?('.vagrant/machines/logstash/secondDisk.vdi')
			logstash_vb.customize ['createhd', '--filename', '.vagrant/machines/logstash/secondDisk.vdi', '--variant', 'Standard', '--size', 10 * 1024]
			end
			logstash_vb.customize ['storageattach', :id,  '--storagectl', 'IDE', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', '.vagrant/machines/logstash/secondDisk.vdi']		
		end
	end

	# VM - MAVEN
	config.vm.define "maven" do |maven|
		maven.vm.hostname = "maven.everis.com"
        	maven.vm.network "public_network", ip: "192.168.1.203"
		maven.vm.provider "virtualbox" do |maven_vb|
			maven_vb.memory = "2048"	
			unless File.exist?('.vagrant/machines/maven/secondDisk.vdi')
			maven_vb.customize ['createhd', '--filename', '.vagrant/machines/maven/secondDisk.vdi', '--variant', 'Standard', '--size', 10 * 1024]
			end
			maven_vb.customize ['storageattach', :id,  '--storagectl', 'IDE', '--port', 1, '--device', 0, '--type', 'hdd', '--medium', '.vagrant/machines/maven/secondDisk.vdi']
		end
	end
        config.vm.provision "ansible" do |ans|
                ans.playbook = "site.yml"
        end
end
