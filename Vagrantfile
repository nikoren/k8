    Vagrant.configure("2") do |config|

          config.vm.define "controller1" do |controller1|
              controller1.vm.provider "virtualbox" do |v|
                v.memory = 3072
                v.cpus = 2
                controller1.ssh.forward_agent = true
              end
              controller1.vm.box = "bento/centos-7"
              controller1.vm.network :private_network, ip: "10.0.99.1"
              controller1.vm.provision :ansible do |ansible|
                ansible.playbook = "ansible/provision-master.yml"
                ansible.extra_vars = {
                    node_ip: "10.0.99.1"
                }
                ansible.raw_arguments = ["--diff", "-v"]
              end
          end


         config.vm.define "worker1" do |worker1|
              worker1.vm.provider "virtualbox" do |v|
                v.memory = 3072
                v.cpus = 2
                worker1.ssh.forward_agent = true
              end

              worker1.vm.box = "bento/centos-7"
              worker1.vm.network :private_network, ip: "10.0.99.2"
              worker1.vm.hostname = "worker1"
              worker1.vm.provision :ansible do |ansible|
                ansible.playbook = "ansible/provision-worker.yml"
                ansible.extra_vars = {
                    node_ip: "10.0.99.2"
                }
                ansible.raw_arguments = ["--diff", "-v"]
              end
        end



         config.vm.define "worker2" do |worker2|
              worker2.vm.provider "virtualbox" do |v|
                v.memory = 3072
                v.cpus = 2
                worker2.ssh.forward_agent = true
              end
              worker2.vm.box = "bento/centos-7"
              worker2.vm.network :private_network, ip: "10.0.99.3"
              worker2.vm.hostname = "worker2"
              worker2.vm.provision :ansible do |ansible|
                ansible.playbook = "ansible/provision-worker.yml"
                ansible.extra_vars = {
                    node_ip: "10.0.99.3"
                }
                ansible.raw_arguments = ["--diff", "-v"]
              end
        end
end
