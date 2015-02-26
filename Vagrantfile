BOX = "puppetlabs/ubuntu-14.04-64-nocm"

Vagrant.configure("2") do |config|
  config.vm.define "development", primary: true do |config|
    config.vm.box = BOX
    config.ssh.forward_agent = true

    config.vm.provider :vmware_fusion do |v|
      v.vmx["memsize"] = "512"
      v.vmx["numvcpus"] = "1"
    end

    config.vm.provision :shell, inline: <<-EOS
bash <(curl -s https://raw.githubusercontent.com/heroku/stack-images/master/bin/cedar-14.sh)
mkdir -p /app && chown vagrant:vagrant /app
EOS
  end
end
