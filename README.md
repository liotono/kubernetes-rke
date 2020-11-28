# kubernetes-rke

This project helps you to bootstrap an environment so you can install kubernetes on it. It uses Vagrant, Ansible, libvirt and RKE.

# Steps to install kubernetes

1. After cloning the repository, issue: vagrant up. This will create the master and worker nodes specified in the Vagrantfile. 
1. Execute the playbook in site.yml. This will do the following:
  1. Update the kubernetes nodes and reboot them to apply updates.
  1. Load the necessary kernel modules to install kubernetes.
  1. Set the necessary kernel parameters to install kubernetes.
  1. Disable swap on the worker nodes.
  1. Install docker on the master and worker nodes.
  1. Install the RKE binary file (https://rancher.com/docs/rke/latest/en/installation/).
  1. Generate a key pair to be distributed to the master and worker nodes.
  1. Install kubectl.
  1. Deploy the file cluster.yml to k8s-master-1 (https://rancher.com/docs/rke/latest/en/config-options/).
1. Log into the master node k8s-master-1.
1. Issue: rke up.
