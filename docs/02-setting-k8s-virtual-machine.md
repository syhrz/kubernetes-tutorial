# Part 2: Setting up K8s Virtual Machine

In this tutorial I provided 2 method to setup the k8s master virtual machine.

    1. Method 1: Manual method by using SSh to the virtual machine.
    2. Method 2: A slight automated way by using ansible.


## Method 1: Manual Installation

### Configure hostname

Depends one the virtual machine we can update the hostname to distinguish the vm's. 

```bash
sudo hostnamectl set-hostname k8s-master
```

And for example we can set for the agent

```bash
sudo hostnamectl set-hostname k8s-agent
```

### Install docker

The first step is to install docker for each kubernetes nodes.

```bash
sudo apt install docker.io
sudo systemctl enable docker
sudo systemctl start docker
```

Check if docker service is active.

```bash
systemctl status docker
```

### Install kubernetes administration tools

First We will need to register the google gpg key.

```bash
wget -qO - https://packages.cloud.google.com/apt/doc/apt-key.gpg | sudo apt-key add -
sudo apt-add-repository "deb http://apt.kubernetes.io/ kubernetes-xenial main"
```

Install kubectl, kubeadm and kubelet

```bash
sudo apt install kubeadm kubectl kubelet
```

You can try to check the versions of each installed package

```bash
kubeadm version
kubectl version
kubelet --version
```

## Method 2: Setup with Ansible

You can find the playbooks inside `ansible/playbooks/k8s-master-setup.yml` and copy the playbook and execute the playbook inside your working directory. 

```bash
cd my-kube
ansible-playbook -i .vagrant/provisioners/ansible/inventory/vagrant_ansible_inventory k8s-master-setup.yml
```
