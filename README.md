# Table of Contents

* [Ubuntu](#ubuntu)
	* [initial](#initial)
	* [Applications](#applications)
	* [Dotfiles](#dotfiles)
	* [Terminal](#terminal)
	* [Development](#development)

# Ubuntu

## Initial

Launch the **Terminal** and view installed packages.

```bash
sudo apt list --installed
```

Remove unwanted packages.

```bash
sudo apt remove [package] [package] ...
```

Update and upgrade packages.

```bash
sudo apt update && sudo apt upgrade
```

Install build essentials.

```bash
sudo apt install build-essential libssl-dev libffi-dev
```

Install restricted extras.

```bash
sudo apt install ubuntu-restricted-extras
```

> **Note**
>
> For copyright reasons, many of these [essential packages](https://en.wikipedia.org/wiki/Ubuntu-restricted-extras) are excluded from Ubuntu's default installation.

Remove  unused packages.

```bash
sudo apt autoremove
```

### Ubutu Pro 

See [Ubunto Pro](https://ubuntu.com/pro) to obtain a token.

```bash
sudo apt install ubuntu-advantage-tools
sudo pro attach [token]
```

## Applications

### Chrome

See [installation guide](https://www.google.com/chrome/).

### Color Picker

```bash
sudo apt install gcolor3
```

### Discord

See [installation guide](https://discord.com/download).

### Dropbox

See [installation guide](https://www.dropbox.com/install-linux).

### FileZilla

```bash
sudo apt install filezilla
```

### Obsidian

See [installation guide](https://obsidian.md/download).

### Slack

See [installation guide](https://slack.com/downloads/linux).

### Spotify

See [installation guide](https://www.spotify.com/us/download/linux/).

### Virtual Box

```bash
sudo apt install virtualbox
```

### Visual Studio Code

See [installation guide](https://code.visualstudio.com/download).

## Dotfiles

See [Dotfiles repository](https://github.com/jcp/dotfiles) for installation instructions.

> **Note**
>
> These dotfiles contain configurations for certain [applications](#applications) within this repository. Install all [applications](#applications) before installing dotfiles.

## Terminal

Install [Tilix](https://gnunn1.github.io/tilix-web/), a tiling terminal emulator.

```bash
sudo apt install tilix
```

Install [Exa](https://the.exa.website/#installation), a replacement for `ls`.

```bash
sudo apt install exa
```

Install [Zsh](https://www.zsh.org/), a **Bash** replacement shell.

```bash
sudo apt install zsh
```

Install [Oh My ZSH], an open source **Zsh** configuration manager framework.

```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Install [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) and [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting).

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-syntax-highlighting ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

### Fonts

Install [Powerline](https://github.com/powerline/fonts) fonts.

```bash
sudo apt install fonts-powerline
```

Install [JetBrains Mono](https://www.jetbrains.com/lp/mono/#how-to-install) fonts.

```bash
sudo mkdir /usr/share/fonts/truetype/jetbrains-mono
# Unpack font files...
fc-cache -f -v
```

> **Note**
> 
> Once installed, set as default for **Tilix** and **Visual Studio Code**.

### Theme

Install [Powerlevel10k](https://github.com/romkatv/powerlevel10k) theme.

```bash
git clone https://github.com/romkatv/powerlevel10k.git $ZSH_CUSTOM/themes/powerlevel10k
```

Install **Tomorrow Night** theme with [Gogh](https://gogh-co.github.io/Gogh/).

```bash
sudo apt install dconf-cli uuid-runtime
bash -c  "$(wget -qO- https://git.io/vQgMr)"
```

## Development

Create **Development** folder.

```bash
mkdir ~/Development
```

### SSH Keys

See [installation guide](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent).

> **Note**
>
> Once generated, add `id_*.pub` to [Ubuntu One](https://login.ubuntu.com/ssh-keys) and [Github](https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account).

### Environments

#### Node.js

See [installation guide](https://github.com/nvm-sh/nvm#installing-and-updating).

> **Note**
> 
> Move appended export code from `~/.zshrc` to `~/.exports`.

#### Python

Install [Pip](https://pypi.org/project/pip/), a Python package installer.

```bash
sudo apt install python3-pip
```

Install [venv](https://docs.python.org/3/library/venv.html), a virtual environment creation tool.

```bash
sudo apt install python3-venv
```