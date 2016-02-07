projectPath = "F:\Projects\"

Vagrant.configure("2") do |config|
	config.vm.provider "virtualbox" do |v|
  		v.memory = 2048
	end
	config.vm.define :skunkworks do |skunkworks|
		skunkworks.vm.box = "trusty-i386"
		skunkworks.vm.box_url = "https://cloud-images.ubuntu.com/vagrant/trusty/current/trusty-server-cloudimg-i386-vagrant-disk1.box"
		skunkworks.vm.hostname = "skunkworks"

		skunkworks.vm.network :forwarded_port, host: 13000, guest: 13000
		skunkworks.vm.network :forwarded_port, host: 10010, guest: 10010
		skunkworks.vm.network :forwarded_port, host: 10011, guest: 10011
		skunkworks.vm.network :forwarded_port, host: 10080, guest: 80
		skunkworks.vm.network :forwarded_port, host: 13306, guest: 3306
		
		skunkworks.vm.synced_folder ".", "/vagrant", disabled: true
		skunkworks.vm.synced_folder projectPath, "/var/www", group: "www-data", mount_options: ['dmode=0775','fmode=0775']
	end
end
