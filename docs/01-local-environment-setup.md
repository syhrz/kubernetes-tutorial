# Part 1: Local Environment Setup

In this part We'll setup some basic requirements that will be needed on setting up kubernetes locally. I mainly use Linux thought this guide should be relevan in MacOS. There are a few prequisites before We can continue:
- virtualbox.
- vagrant.

You can install them with your favorite package manager or check if both already installed by running these commands.

```bash
vagrant version
virtualbox
```

Then We can start with an empty directory. 

```bash
mkdir kubernetes-at-home
cd kubernetes-at-home
```

By using vagrant We can initialize and run a virtual machine very easly using terminal. In this guide I'm using Ubuntu Bionic since it's a quite common OS.

```bash
vagrant init ubuntu/bionic64
vagrant up --provide virtualbox
```

Alright let's wait for a few minutes until the virtual machine completely running. You can check the status of the virtual machines that managed by vagrant by calling this command in any directory.

```bash
vagrant global-status
```

After the virtual machine state is `running`, We can get inside it by using this command inside the directory

```bash
vagrant ssh
```

Try to update and upgrade the virtual machine operating system then exit.

```bash
sudo apt update
sudo apt upgrade --yes
exit
```

Alright that's all for this, in the next part We will setting up the virtual machine to run kubernetes inside it.
