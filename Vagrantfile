Vagrant.configure("2") do |config|
  #Зеркало доступное в РФ
  ENV['VAGRANT_SERVER_URL'] = 'https://vagrant.elab.pro'

  config.vm.box = "ubuntu/jammy64"

  #VirtualBox
  config.vm.provider "virtualbox" do |vb|
    vb.memory = "2048"
    vb.cpus = 2
  end

  # PostgreSQL
  config.vm.provision "shell", inline: <<-SHELL
  
    apt-get update
    
    apt-get install -y wget gnupg

    wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | sudo tee /etc/apt/trusted.gpg.d/pgp.asc
    echo "deb http://apt.postgresql.org/pub/repos/apt/ jammy-pgdg main" | sudo tee /etc/apt/sources.list.d/pgdg.list

    apt-get update

    apt-get install -y postgresql-12 postgresql-contrib-12

    psql --version
  SHELL
end
