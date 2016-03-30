# -*- mode: ruby -*-
# vi: set ft=ruby :

# All Vagrant configuration is done below. The "2" in Vagrant.configure
# configures the configuration version (we support older styles for
# backwards compatibility). Please don't change it unless you know what
# you're doing.
Vagrant.configure(2) do |config|
  
  ###################################################
  ## Run latest version of Docker on openSUSE 13.2 ##
  ###################################################

  #Create VM with openSuse 13.2
  #----------------------------
  config.vm.box = "webhippie/opensuse-13.2"
  config.vm.provider "virtualbox" do |vb|
      vb.memory = "1024"
      vb.cpus = 1
    end

  #Install latest version of Docker once the VM is running up
  #----------------------------------------------------------
  config.vm.provision "shell", inline: <<-SHELL
    #sudo zypper -n update 
    sudo zypper -n install git
    git clone https://github.com/jvalderrama/suse-challenge-1.git
    cd suse-challenge-1
    sudo ./install/suse/install-docker

    ##########################################################################
    ## Introduce an error inside of the Dockerfile and then start the build ##
    ##########################################################################

    #Introduce the error in the Dockerfile as Suse suggested for the challenge
    #------------------------------------------------------------------------
    cat > Dockerfile << EOF
         FROM busybox
         MAINTAINER Jorge Valderrama <joedval@gmail.com>
         RUN touch /hello
         RUN boom
EOF
  SHELL
end
