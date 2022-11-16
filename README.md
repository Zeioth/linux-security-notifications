# linux-security-notifications
Systemd service that displays important security information as friendly desktop notifications.

# FEATURE 1 - Notifications about potentially dangerous file permissions.
Think about Android. It tells you the permissions used by the programs you are about to install. So convenient right? How come we don't have anything like that on the Linux desktop yet? Well, it's a bit more complicated. In practice, only the revierews of your distro repositories could provide you that information. And they won't because it's a titanic work they are not paid for.

Then what can we do? Plently! The approach of this project is to periodically compare the permissions of all the files of your system with the permissions they had 10 minutes ago. If any program you recently installed, installed files with a privilege level upper than 644, you will get a desktop notification about those files, so you can manually review them and see what's going on.

# FEATURE 2 - Notifications about unwanted users accessing your system
If someone tries to log into your system (locally, or remotely), and fail to introduce the right password, you will get a desktop notification.

# FEATURE 3 - Notifications about incorrect sudo configurations (NOT IMPLEMENTED YET)
In case an user might potentially have a dangerous sudo/user/group configurations, we will warn him.

# FEATURE 4 - Notifications about keyloggers (NOT IMPLEMENTED YET)
If someone is recording out keystrokes, send a desktop notifications.

Again, this feature provide alerts, which is convenient, but if you are really concerned about your acess security, it's a good idea to encrypt your hard disks to EXT4 + LUKS is a good idea on the local side, and audit your ssh settings, and firewall, for the net.

# FAQ

* **Hey, but you are notifing file permissions AFTER the program is installed, isn't it that dangerous?**: Well, yes. It's not ideal, and if you are truly concerned about the security of your computer, you should go to the source code of the program you are about to install, and read it first. But we all know most desktop users, won't do it, and this solutions is WAY better than nothing. It is convenient.
* **Access breach notifications? But that's SO unlikely**: Yes it is. But there you go.
* **What if I don't want to use sudo? Are you gonna send me notifications?:** Yes. But if you have that case of use, you probably won't be using this package at all. If I'm wrong here, we could add a config option to disable this alert in the future.
* **Keyloggers? But I use wayland!:** On the user space, wayland offers a good level of protection, but keyloggers can still bypass that protection and record our keyboard if they somehow get sudo permissions.
