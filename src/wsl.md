# How to use ArchLinux in WSL2

This tutorial will be like a step-by-step tutorial. Just follow it below. Understand that each topic is in which environment you should run some commands or do something, let's begin.

## Powershell
> Download [wsl2](https://docs.microsoft.com/en-us/windows/wsl/wsl2-kernel)

- Run: 
```
wsl --set-default-version 2
```

## Windows

> Download [ArchWSL](https://github.com/yuk7/ArchWSL)

> Create a folder (like `C:\Arch`) and run the .exe there.

## Arch (root)

- Refresh Pacman GPG keys:
```
pacman-key --init
pacman-key --populate
pacman-key --refresh-keys
pacman-Sy archlinux-keyring
pacman -Syyu
```
> The third command will take too long and thats normal. The last command is an update command, remember to keep your environment updated.

- Install zsh: (my preference here, but you can keep bash if you want to). 
```
pacman -S zsh
```

- Create a new user:
```
groupadd sudo
nano /etc/sudoers

UNCOMMENT THESE LINES:
%wheel ALL=(ALL) NOPASSWD: ALL 
%sudo   ALL=(ALL) ALL

ctrl o; enter; ctrl x

useradd -m -G wheel,sudo -s /bin/zsh <username> (or /bin/bash)
passwd <username>
```
Close Arch for a bit.

## Powershell
- Go where you saved your Arch.exe and run this:
```
Arch.exe config --default-user <username>
```

## Arch (``<username>``)
- Install AUR helper (yay)
```
sudo pacman -S git openssh
sudo pacman -S base-devel
git clone https://aur.archlinux.org/yay-git.git
cd yay-git
makepkg -si
yay -Syu
rm -rf ~/yay-git
```
- some useful console tools:
```
sudo pacman -S mc wget htop pv ccze
```
From this point you already have Arch Linux configured in your WSL, now I'll pass some things that were useful for me as developer, this is close to my environment, fell free to have it.

## Optional tools

### Creating ssh key
- To create a ssh key and copying it is simple, just run two commands, the first one creates it and the second one to copy (then you paste on your github, gitlab, bitbucket, anywhere you want, be wise).
```
ssh-keygen
cat ~/.ssh/id_ed25519.pub
```
### ASDF - never install programming languages anymore.
- I prefer to pass the official documentation from [asdf](https://asdf-vm.com/) and you choose the best option to install it.

- check if you have git and curl installed, if you dont:
```
pacman -S curl git
```

- download asdf (this tutorial were made in December 2023 it may be not updated).
```
git clone https://github.com/asdf-vm/asdf.git ~/.asdf
```

- install it by setting on plugins:
```
nano ~/.zshrc
plugins=(
    asdf
    //other plugins here
    )
```
- check the documentation to use it

### PowerLevel10k - personalize your Arch
