# Table of Contents

* [Dual Boot Windows 10 / Ubuntu 19.04](#dual-boot-windows-10--ubuntu-1904)
	* [Windows](#windows)
	* [Ubuntu](#ubuntu)

* [Ubuntu Configuration](#ubuntu-configuration)
	* [Initial](#initial)
	* [Dotfiles](#dotfiles)
	* [Theme](#theme)
	* [SSH Keys](#ssh-keys)
	* [Essential Packages](#essential-packages)

* [Commands](#commands)

* [Shortcuts](#shortcuts)
	* [Keyboard](#keyboard)
	* [Visual Studio Code](#visual-studio-code)

# Dual Boot Windows 10 / Ubuntu 19.04

## Windows

### Create a Backup

* Hit <kbd>⊞ win</kbd> + <kbd>r</kbd>.
* Enter `control` and hit <kbd>enter</kbd>.
* Select **Backup and Restore (Windows 7)**.
* Select **Create a system image** and follow steps.

### Disable Fast Startup

* Hit <kbd>⊞ win</kbd> + <kbd>r</kbd>.
* Enter `control` and hit <kbd>enter</kbd>.
* Select **Hardware and Sound**.
* Select **Change what the power buttons do** under **Power Options**.
* Uncheck **Turn on fast startup (recommended)**.
* Hit <kbd>enter</kbd>.

### Disable Secure Boot

* Hold <kbd>shift</kbd> and restart.
* Select **Troubleshoot** > **Advanced options** > **UEFI Firmware Settings** > **Restart**
* Once in UEFI, select **Security** > **Secure Boot** and set **Secure Boot Support** to **Disabled**.
* Save to restart.

> **Note**
>
> UEFI interface may differ based on vendor specifications.

### Shrink Partition

* Hit <kbd>⊞ win</kbd> + <kbd>r</kbd>.
* Enter `diskmgmt.msc` and hit <kbd>enter</kbd>.
* Right click a volume and select **Shrink Volume...**
* Enter the amount of space to shrink and hit <kbd>enter</kbd>.

### Create Installer

For this step, a 4GB+ USB flash drive is required.

* Download latest version of [Ubuntu Desktop](https://ubuntu.com/download/desktop).
* Download [Rufus](https://rufus.ie/) to create a bootable USB drive.
* Insert USB flash drive and open **Rufus**.
* Hold <kbd>f11</kbd> and restart. This will boot Ubuntu from the USB drive.

> **Note**
> 
> Shortcut to boot from USB drive may differ based on vendor specifications.

## Ubuntu

### Install Ubuntu

* From the GRUB screen, select **Install Ubuntu**.
* Proceed through the installation process.
* On the **Updates and other software** screen, check **Normal installation**, uncheck all other options and select **Continue**.
* On the **Installation type** screen, select **Something else** and select **Continue**.
* On the partition screen, follow the [partition space allocation](#partition-space-allocation) steps below to allocate space for `root`, `home` and `swap`.
* Once the partitions have been created, select **Install Now** and then select **Continue**.
* Proceed through the remaining installation steps. When finished, Ubuntu will restart. If the computer boots directly to Windows, see [changing boot order](#changing-boot-order) below.

#### Partition Space Allocation

For each partition, select the **free space** partition and select the **+** sign.

* `root`: Allocate 20GB of space and set **Mount point** to `/`.
* `swap`: Allocate 32GB of space and set **Use as** to `swap area`.
* `home`: Allocate the remaining space and set **Mount point** to `/home`.

> **Note**
>
> * See Ubuntu's [SwapFaq](https://help.ubuntu.com/community/SwapFaq) guide for more information on **swap** space allocation.

#### Changing Boot Order

* Hold <kbd>shift</kbd> and restart.
* Select **Troubleshoot** > **Advanced options** > **UEFI Firmware Settings** > **Restart**
* Once in UEFI, find the boot order settings and give Ubuntu priority.
* Save and restart.

> **Note**
>
> * Boot order settings may differ based on vendor specifications.

# Ubuntu Configuration

## Initial

### Remove Unwanted Packages, Upgrade and Update

Launch the **Terminal** and view installed packages.

```bash
$ sudo apt list --installed
```

Remove unwanted packages.

```bash
$ sudo apt remove [package] [package] ...
```

Update and upgrade packages.

```bash
$ sudo apt update && sudo apt upgrade
```

### Install Restricted Extras

Due to copyright reasons, many of these [essential packages](https://en.wikipedia.org/wiki/Ubuntu-restricted-extras) are excluded from Ubuntu's default installation.

```bash
$ sudo apt install ubuntu-restricted-extras
```

### Install drivers

Check to see what drivers exists.

```bash
$ sudo ubuntu-drivers devices
```

Install any missing or recommended drivers.

```bash
$ sudo apt install nvidia-driver-418
```

Ensure that the new drive is installed and selected.

```bash
$ prime-select query
nvidia
```

> **Notes**
>
> * If PRIME doesn't exist, restart computer and try again.
> * See `prime-select --help` for option on switching between drivers.

### Install Build Essentials

```bash
$ sudo apt install -y build-essential curl git libbz2-dev libffi-dev liblzma-dev libncurses5-dev libncursesw5-dev libreadline-dev libsqlite3-dev libssl-dev llvm make python-openssl tk-dev vim wget xz-utils zlib1g-dev 
```

### Cleanup

Remove  unused packages.

```bash
$ sudo apt autoremove
```

## Dotfiles

Use the [Dotfiles repository](https://github.com/jcp/dotfiles) instructions.

> **Note**
>
> These dotfiles contain configurations for certain packages within this repository.

## Theme

Install [Tweaks](https://wiki.gnome.org/Apps/Tweaks).

```bash
$ sudo apt install gnome-tweak-tool
```

Load [dconf](https://wiki.gnome.org/action/show/Projects/dconf) settings.

```bash
$ curl https://raw.githubusercontent.com/jcp/dotfiles/master/.dconf
$ dconf load / < .dconf
$ rm .dconf
```

### Terminal

Use [Gogh](https://github.com/Mayccoll/Gogh) to install the **Tomorrow Night** theme for the **Terminal**.

```bash
$ sudo apt install dconf-cli uuid-runtime
$ bash -c  "$(wget -qO- https://git.io/vQgMr)"
```

Install [Powerline Fonts](https://github.com/powerline/fonts).

```bash
$ sudo apt install fonts-powerline
```

Install [exa](https://the.exa.website) replacement for `ls`.

```bash
$ sudo apt install exa
```

### ZSH and Oh My ZSH

Before installing, see [Dotfiles](#dotfiles).

#### ZSH

```bash
$ sudo apt install zsh
```

#### Oh My ZSH

```bash
$ sh -c "$(curl -fsSL https://raw.github.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

Install two custom plugins: `zsh-autosuggestions` and `zsh-syntax-highlighting`.

```bash
$ git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
$ git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

Install Powerlevel10k theme.

```bash
$ git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

## SSH Keys

Generate SSH keys.

```bash
$ ssh-keygen -t rsa -b 4096 -C "me@jcp.io"
```

Add to ssh-agent

```bash
$ eval "$(ssh-agent -s)"
$ ssh-add ~/.ssh/id_rsa
```

## Essential Packages

### Blender

```bash
$ sudo snap install blender --classic
```

### Cheese

```bash
$ sudo apt install cheese
```

### Chrome

[Installation guide](https://www.google.com/chrome/)

### Discord

```bash
$ sudo snap install discord
```

### Docker

```bash
$ curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
$ sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable edge"
$ sudo apt update
$ sudo apt install -y docker-ce
```

### Dropbox

[Installation guide](https://www.dropbox.com/install-linux)

### FileZilla

```bash
$ sudo apt install filezilla
```

### Gazebo

```bash
$ sudo sh -c 'echo "deb http://packages.osrfoundation.org/gazebo/ubuntu-stable `lsb_release -cs` main" > /etc/apt/sources.list.d/gazebo-stable.list'
$ wget http://packages.osrfoundation.org/gazebo.key -O - | sudo apt-key add -
$ sudo apt update
$ sudo apt install gazebo9
```

### Git

Before installing, see [Dotfiles](#dotfiles).

```bash
$ sudo apt install git
```

Add `id_rsa.pub` to [Github](https://github.com/settings/keys).

```bash
$ cat ~/.ssh/id_rsa.pub
```

### Gnome Sushi

```bash
$ sudo apt install gnome-sushi
```

### Go

Before installing, see [Dotfiles](#dotfiles).

```bash
$ sudo add-apt-repository ppa:longsleep/golang-backports
$ sudo apt update
$ sudo apt install golang-go
$ sudo mv ~/go ~/.go
```

> **Note**
>
> Moving `go` to `.go` is a personal preference.

### Gobuster

```bash
$ go get github.com/OJ/gobuster
$ sudo ln -s ~/.go/bin/gobuster /usr/bin/gobuster
```

### Gpick

```bash
$ sudo apt install gpick
```

### Heroku CLI

```bash
$ sudo snap install heroku --classic
```

### MongoDB

```bash
$ sudo apt install mongodb
```

### NMAP

```bash
$ sudo apt install nmap
```

### NVM and Node.js

Before installing, see [Dotfiles](#dotfiles).

```bash
$ curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.34.0/install.sh | bash
$ nvm install node
```

#### PostgreSQL

```bash
$ sudo apt update
$ sudo apt install postgresql postgresql-contrib postgresql-client postgresql-client-common libpq-dev
```

### Pyenv, Python and Pipenv

Before installing, see [Dotfiles](#dotfiles).

#### Pyenv

```bash
$ curl https://pyenv.run | bash
$ source ~/.zshrc
```

#### Python

```bash
$ pyenv install -v 3.6.9
$ pyenv install -v 3.7.4
$ pyenv install -v 3.8-dev
```

Set desired version of Python.

```bash
$ pyenv global 3.7.4
```

#### Pipenv

```bash
$ sudo apt install software-properties-common
$ sudo add-apt-repository ppa:pypa/ppa
$ sudo apt update
$ sudo apt install pipenv
```

### Slack

```bash
$ sudo snap install slack --classic
$ sudo apt update 
$ sudo apt upgrade slack-desktop
```

### Spotify

```bash
$ sudo snap install spotify
```

### Tilix

See, [Terminal](#terminal) to install the **Tomorrow Night** theme for Tilix.

```bash
$ sudo bash install tilix
```

### TrueCrypt

```bash
$ sudo add-apt-repository ppa:stefansundin/truecrypt
$ sudo apt update
$ sudo apt install truecrypt
```

### Typora

```bash
$ wget -qO - https://typora.io/linux/public-key.asc | sudo apt-key add -
$ sudo add-apt-repository 'deb https://typora.io/linux ./'
$ sudo apt install typora
```

### Visual Studio Code

```bash
$ sudo snap install code --classic
```

# Commands

Dump and load `dconf`.

```bash
$ dconf dump / > .dconf
$ dconf load / < .dconf
```

List installed packages.

```bash
$ apt list --installed
```

Switch drivers.

```bash
$ sudo prime-select query
$ sudo prime-select intel
$ sudo prime-select nvidia
```

Access PostgreSQL.

```bash
$ sudo -u postgres psql
```

# Shortcuts

## Keyboard

| Shortcut | Description |
| -------- | ----------- |
| <kbd>alt</kbd> + <kbd>1</kbd> | Maximize application |
| <kbd>alt</kbd> + <kbd>2</kbd> | Move application to split screen, left side |
| <kbd>alt</kbd> + <kbd>3</kbd> | Move applicatoin to split screen, right side |

## Visual Studio Code

| Shortcut | Description |
| -------- | ----------- |
| <kbd>shift</kbd> + <kbd>alt</kbd> + <kbd>i</kbd> | Multi line cursor at end of selection |
| <kbd>shift</kbd> + <kbd>alt</kbd> + <kbd>down</kbd> | Multi line cursor (down) |
| <kbd>shift</kbd> + <kbd>alt</kbd> + <kbd>up</kbd> | Multi line cursor (up) |

> **Note**
>
> For more, see https://code.visualstudio.com/Docs/editor/codebasics.