# Part 1: Local Environment Setup

In this part We'll setup some basic requirements that will be needed on setting up kubernetes locally. I mainly use Linux thought this guide should be relevan in MacOS. Before continue please get familiar with these softwares:
- [Virtualbox](https://www.virtualbox.org/).
- [Vagrant](https://www.vagrantup.com/).
- Ansible.

For virtualbox and vagrant You can install them with your favorite package manager or check if both already installed by running these commands.

```bash
vagrant version
vboxmanage --version
```

Then We can start with an empty directory. 

```bash
mkdir my-kube
cd my-kube
vagrant init ubuntu/xenial64
```

We'd like to add a few automation in the virtual machine so open the Vagrantfile with your favorite text editor and add these few lines to install the latest version of ansible.
```bash
...
    config.vm.provision "shell", inline: <<-SHELL
        apt update
        apt install software-properties-common
        apt-add-repository --yes --update ppa:ansible/ansible
        apt install --yes ansible
    SHELL
end       
```

Then spin up the virtual machine
```bash
vagrant up
```

Alright let's wait for a few minutes until the virtual machine completely running. You can check the status of the virtual machines that managed by vagrant by calling this command in any directory.

```bash
vagrant global-status
```

After the virtual machine state is `running`, We can get inside it by using this command inside the directory

```bash
vagrant ssh
```

Try to run a few command, for example let's check ansible version.

```bash
ansible --version
exit
```

Alright that's all for this, in the next part We will setting up the virtual machine to run kubernetes inside it.
