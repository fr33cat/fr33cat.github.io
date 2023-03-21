Here’s a tutorial on how to use a YubiKey to authenticate via SSH to a linux (debian) host:

First, make sure you have OpenSSH version 8.2 or higher installed on your server. If you’re using Debian Buster (stable), it delivers version 7.9 so you’ll need to install a newer version via Debian Buster Backports1. Edit /etc/apt/sources.list and add the following line: deb http://deb.debian.org/debian buster-backports main. Then update the package list and update openssh-server: apt update and apt-get -t buster-backports install "openssh-server"1.

Next, create FIDO U2F keys on your local machine: ssh-keygen -t ecdsa-sk -f ~/.ssh/id_ecdsa_sk. You may want to repeat this step with your backup stick: ssh-keygen -t ecdsa-sk -f ~/.ssh/id_ecdsa_sk21.

You can use these new public keys like your old ones (without FIDO). Just put them on your server: ssh-copy-id -i ~/.ssh/id_ecdsa_sk.pub YOUR_SERVER_NAME and repeat for backup stick: ssh-copy-id -i ~/.ssh/id_ecdsa_sk2.pub YOUR_SERVER_NAME. Or you can copy the content of the files id_ecdsa_sk.pub and id_ecdsa_sk2.pub into the file .ssh/authorized_keys on your server1.

If you previously used normal public key authentication without FIDO U2F you may want to remove the old key in it. If you now open a new ssh connection your Yubikey has to be connected to your PC and you have to touch it to establish the connection1.
