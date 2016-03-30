# suse-challenge-1
Suse Challenge One for Madrid

#Explanation for the problem (Debug and how it was solved)

## 1. Create a test environment

The first thing is to have a fast and ready environment to reproduce the challenge
proposed, therefore the use of ``Vagrant`` can be suitable due the situation, just install
it (https://www.vagrantup.com/) on your Laptop and must be install ``VirtualBox`` also 
(https://www.virtualbox.org/wiki/Downloads).

## 2. Install openSuse 13.2 

With the use of Vagrant and VirtualBox, let's find an image for the OS required, it can be 
found in [openSuse 13.2](https://atlas.hashicorp.com/webhippie/boxes/opensuse-13.2) so creating 
a [Vagrantfile](https://github.com/jvalderrama/suse-challenge-1/blob/master/Vagrantfile)
specifying the OS and resources for the new VM.

## 3. Install last version of Docker in openSuse 13.2

Once the VM is running up, just clone the current repository in the new VM and [install Docker
through a script](https://github.com/jvalderrama/suse-challenge-1/blob/master/install/suse/install-docker) and the use of the same [Vagrantfile](https://github.com/jvalderrama/suse-challenge-1/blob/master/Vagrantfile)

## 4. Create and introduce the error in the Dockerfile

With all the pre-requisites running up, just ``create a Dockerfile like has been suggested for the
challenge``, one more time using the [Vagrantfile](https://github.com/jvalderrama/suse-challenge-1/blob/master/Vagrantfile)

## 5. Reproduce the error, fix it and create the new image

Once created the ``Dockerfile`` with the error, has been created a [new script] 
(https://github.com/jvalderrama/suse-challenge-1/blob/master/postinstall/flow) just to have
a 'flow',it means reproduce the error building the new image with Docker, later we fix it 
deleting the line that produce the error and finally building the image again.

To check just listing the images created and should be appear two images, the busybox and the new image
without name.

# Launch the challenge automatically

1. Install vagrant and VirtualBox, read the Explanation of the Problem above

2. In the laptop just clone the repository 
   ``git clone https://github.com/jvalderrama/suse-challenge-1.git``

3. Go inside the folder suse-challenge-1
   ``cd suse-challenge-1``

4. Start up the VM 
   ``vagrant up``

5. Go into the VM using ssh
   ``vagrant ssh``

6. Go inside the folder suse-challenge-1
   ``cd suse-challenge-1``

7. Check the file Dockerfile with the error
   ``cat Dockerfile``

8. Execute the flow to complete the challenge
   ``./postinstall/flow``

9. Check again by yourself the Dockerfile and the images created
   ``cat Dockerfile``
   ``docker images``

That's all, challenge resolved. :)

