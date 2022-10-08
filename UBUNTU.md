# Ubuntu

Configure a new [Ubuntu](https://ubuntu.com/) installation.

## Table of Contents

* [Initial](#initial)
* [Applications](#applications)
* [Dotfiles](#dotfiles)
* [Desktop](#desktop)
* [Terminal](#terminal)
* [Development](#development)
* [Shortcuts](#shortcuts)

## Initial

Launch the **Terminal** and view installed packages.

```shell
sudo apt list --installed
```

Remove unwanted packages.

```shell
sudo apt remove [package] [package] ...
```

Update and upgrade packages.

```shell
sudo apt update && sudo apt upgrade
```

Install build essentials.

```shell
sudo apt install build-essential libssl-dev libffi-dev
```

Install restricted extras.

```shell
sudo apt install ubuntu-restricted-extras
```

> **Note**
>
> For copyright reasons, many of these [essential packages](https://en.wikipedia.org/wiki/Ubuntu-restricted-extras) are excluded from Ubuntu's default installation.

Remove  unused packages.

```shell
sudo apt autoremove
```

### Ubutu Pro

See [Ubunto Pro](https://ubuntu.com/pro) to obtain a token.

```shell
sudo apt install ubuntu-advantage-tools
sudo pro attach [token]
```

## Applications

### 1Password

See [installation guide](https://1password.com/downloads/linux/).

### Chrome

See [installation guide](https://www.google.com/chrome/).

### Color Picker

```shell
sudo apt install gcolor3
```

### Discord

See [installation guide](https://discord.com/download).

### Dropbox

See [installation guide](https://www.dropbox.com/install-linux).

### FileZilla

```shell
sudo apt install filezilla
```

### Git

```shell
sudo apt install git
```

### Obsidian

See [installation guide](https://obsidian.md/download).

### Slack

See [installation guide](https://slack.com/downloads/linux).

### Spotify

See [installation guide](https://www.spotify.com/us/download/linux/).

### Virtual Box

```shell
sudo apt install virtualbox
```

### Visual Studio Code

See [installation guide](https://code.visualstudio.com/download).

### Wireshark

See [installation guide](https://www.wireshark.org/download.html). Once installed, enable for non-root users and  **jcp**.

```shell
sudo dpkg-reconfigure wireshark-common
sudo usermod -a -G wireshark jcp
sudo reboot
```

## Dotfiles

See [installation guide](https://github.com/jcp/dotfiles).

> **Note**
>
> These dotfiles contain configurations for certain [applications](#applications) within this repository. Install all [applications](#applications) before installing dotfiles.

## Desktop

Move **Applications** icon to the top of the **Dock**.

```shell
gsettings set org.gnome.shell.extensions.dash-to-dock show-apps-at-top true
```

Show **Trash** icon on Desktop.

```shell
gsettings set org.gnome.shell.extensions.ding show-trash true
```

## Terminal

Install [Tilix](https://gnunn1.github.io/tilix-web/), a tiling terminal emulator.

```shell
sudo apt install tilix
```

Install [Exa](https://the.exa.website/#installation), a replacement for `ls`.

```shell
sudo apt install exa
```

Install [Zsh](https://www.zsh.org/), a **Bash** replacement shell.

```shell
sudo apt install zsh
```

Install [Oh My Zsh](https://github.com/ohmyzsh/ohmyzsh), an open source **Zsh** configuration manager framework.

```shell
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Install [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) and [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting).

```shell
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### Fonts

Install [Powerline](https://github.com/powerline/fonts) fonts.

```shell
sudo apt install fonts-powerline
fc-cache -f -v
```

Install [JetBrains Mono Nerd](https://github.com/ryanoasis/nerd-fonts/releases) fonts.

```shell
wget https://github.com/ryanoasis/nerd-fonts/releases/latest/download/JetBrainsMono.zip
sudo unzip JetBrainsMono.zip -d /usr/share/fonts/jetbrains-mono
rm JetBrainsMono.zip
fc-cache -f -v
```

> **Note**
>
> Once installed, set as default for **Tilix** and **Visual Studio Code**.

### Theme

Install [Powerlevel10k](https://github.com/romkatv/powerlevel10k) theme.

```shell
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

Install **Tomorrow Night** theme with [Gogh](https://gogh-co.github.io/Gogh/).

```shell
sudo apt install dconf-cli uuid-runtime
bash -c  "$(wget -qO- https://git.io/vQgMr)"
```

## Development

Create **Development** folder.

```shell
mkdir ~/Development
```

### SSH Keys

See [installation guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

> **Note**
>
> Once generated, add `id_*.pub` to [Ubuntu One](https://login.ubuntu.com/ssh-keys) and [Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

### Environments

#### Docker

See [installation guide](https://docs.docker.com/engine/install/ubuntu/#set-up-the-repository).

#### Node.js

See [installation guide](https://github.com/nvm-sh/nvm#installing-and-updating).

> **Note**
>
> Move any appended export code from `~/.zshrc` to `~/.exports`.

#### Python

Install [Pip](https://pypi.org/project/pip/), a Python package installer.

```shell
sudo apt install python3-pip
```

Install [venv](https://docs.python.org/3/library/venv.html), a virtual environment creation tool.

```shell
sudo apt install python3-venv
```

### Shortcuts

#### Windows

| Shortcut | Description |
| -------- | ----------- |
| <kbd>Super</kbd> + <kbd>Tab</kbd> | Application switcher |
| <kbd>Super</kbd> + <kbd>▲</kbd> | Maximize window state |
| <kbd>Super</kbd> + <kbd>▼</kbd> | Default window state |
| <kbd>Super</kbd> + <kbd>◄</kbd> | Split window left |
| <kbd>Super</kbd> + <kbd>►</kbd> | Split window right |
