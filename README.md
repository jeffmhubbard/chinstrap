# chinstrap.zsh

A simple one-shot install script for [***Penguin***](https://penguin.fyi) and is a component of [penguin-iso](https://code.linuxit.us/penguin-iso). It is based on the steps described in the [Arch Linux Installation Guide](https://wiki.archlinux.org/index.php/Installation_guide). It only provides a basic framework for installation and navigates the `chroot` for you. You will need basic Linux and shell scripting (`zsh`) knowledge to use this.

This script does not configure the live system or connect to the network. If you need a special keymap or language, you must configure that yourself. You **must be connected to the Internet** for the script to run.

While it is expected that you will customize the script to your needs, it does include all the needed options to do a full installation. These defaults were kept simple to make it easy to evaluate [***Penguin***](https://penguin.fyi) . There are also a few examples of different options in the script as well.

## Configuration
**You must edit the script before running it!**

Some common options are provided at the top of the script for convenience. 
```sh
# settings for new systems
newuser="tux"
hostname=$(uname -n)
keymap="us"
vcfont="default8x16"
locale="en_US"
timezone="America/Chicago"

# install full desktop
packages=(
  penguin-base
  penguin-desktop
  penguin-defaults
)
# kernel
packages+=(linux-zen)
# video drivers
packages+=(xorg-packages)

# WILL USE ENTIRE DISK
rootdev=/dev/sda
```
Additionally, anything else you might need to do during installation can be added or removed by editing the *stages* directly.

## Usage
**STOP!** This script will **PARTITION AND FORMAT** your disks. The default disk is `/dev/sda`. Please read and edit the script before continuing.

Then run `./chinstrap.zsh`. There will be only one prompt before the installation begins. Press `Enter` to continue, or `Ctrl+c` to cancel.

The installation should proceed without need of interaction for several minutes. It will automatically prepare the target disks, install software packages, and configure the new system. Once that is complete, you will be prompted to enter passwords for `$newuser` and `root`.

That's it. Just type `y` at the prompt to reboot.
