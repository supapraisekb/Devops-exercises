Create a Linux  Virtual Machine on your computer. 

Check the distribution, which package manager it uses (yum, apt, apt-get). Which 

CLI editor is configured (Nano, Vi, Vim). 

What software center/software manager it uses. 

Which shell is configured for your user.


**SOLUTION**
1. Created a Vagrant Linux Ubuntu Vm with Oracle VirtualBox
![Vagrant VM Oracle VirtualBox](/screenshots/created-vm-sc.JPG)

![Login Screen Showing the Ubuntu Version](/screenshots/vm-login.JPG)


2. Information on the OS relase and the package manager installed on it

OS release information is gotten by using the command 

```cat /etc/os_release``` 

Package manager information is gotten using the command

```which apt```

![Os Release Info and packege installer Info](/screenshots/OS-release-and-package-installer.JPG)


3. ![Screenshot of Vim installed on the OS](/screenshots/vim-installed.JPG)

