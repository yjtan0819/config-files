# Laptop Setup Configuration

This repository contains configuration files for setting up a new macOS laptop with your preferred development environment.

## Contents

- **`.zshrc`** - Zsh shell configuration with Oh My Zsh and Powerlevel10k theme
- **`.gitconfig`** - Git configuration with user info
- **`vscode-settings.json`** - VS Code settings for editor preferences and extensions
- **`Brewfile`** - Homebrew packages to install
- **`SETUP_INSTRUCTIONS.md`** - This file

## Prerequisites

- macOS system
- Homebrew installed: `/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"`

## Setup Instructions

### 1. Install Homebrew Packages

```bash
cd path/to/this/repo
brew bundle
```

### 2. Set up Zsh Shell

If Zsh is not already installed:
```bash
brew install zsh
```

Install Oh My Zsh:
```bash
sh -c "$(curl -fsSL https://raw.githubusercontent.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```

Install Powerlevel10k theme:
```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

Copy the shell configuration:
```bash
cp .zshrc ~/.zshrc
# Copy the p10k.zsh file if you have it in this repo
cp p10k.zsh ~/.p10k.zsh 2>/dev/null || true
```

Reload your shell:
```bash
source ~/.zshrc
```

### 3. Configure Git

Copy the git configuration:
```bash
cp .gitconfig ~/.gitconfig
```

**IMPORTANT:** Update with your work email and name:
```bash
git config --global user.name "Your Work Name"
git config --global user.email "your.work.email@company.com"
```

Verify your git configuration:
```bash
git config --global user.name
git config --global user.email
```

### 4. Configure VS Code

1. Open VS Code
2. Go to `Code > Preferences > Settings` (or press `Cmd + ,`)
3. Click the "Open Settings (JSON)" button in the top right
4. Copy the contents from `vscode-settings.json` into your settings.json

Alternatively, you can copy the settings file directly:
```bash
cp vscode-settings.json ~/Library/Application\ Support/Code/User/settings.json
```

### 5. Install VS Code Extensions

Install the following extensions from the VS Code marketplace:
- Prettier - Code formatter
- GitHub Copilot
- One Dark Pro (Theme)
- Material Icon Theme
- Code Runner
- Docker
- Python
- Go
- Live Server
- Git Lens
- REST Client
- YAML
- Kubernetes
- Office Viewer
- Pets

Or install them via command line:
```bash
code --install-extension esbenp.prettier-vscode
code --install-extension GitHub.copilot
code --install-extension zhuangtongfa.Material-theme
code --install-extension PKief.material-icon-theme
code --install-extension formulahendry.code-runner
code --install-extension ms-azuretools.vscode-docker
code --install-extension ms-python.python
code --install-extension golang.Go
code --install-extension ritwickdey.LiveServer
code --install-extension eamodio.gitlens
code --install-extension humao.rest-client
code --install-extension redhat.vscode-yaml
code --install-extension ms-kubernetes-tools.vscode-kubernetes-tools
code --install-extension cweijan.vscode-office
code --install-extension tonybaloney.vscode-pets
```

### 6. Configure Terminal Font

The VS Code terminal uses the "MesloLGS NF" font. This should be installed via Homebrew:
```bash
brew install --cask font-meslo-lg-nerd-font
```

Then set it in VS Code settings (already included in `vscode-settings.json`).

## Customization

### Powerlevel10k Theme Configuration

To customize your Powerlevel10k theme:
```bash
p10k configure
```

This will create/update your `~/.p10k.zsh` file.

### Shell Aliases

You can add custom aliases to your shell by creating:
```bash
~/.oh-my-zsh/custom/aliases.zsh
```

### VS Code Settings

For machine-specific settings (like Python interpreter paths), create a `.vscode/settings.json` in your project directory instead of changing global settings.

## Troubleshooting

### Zsh Autosuggestions Not Working
Make sure the plugin is properly sourced in `.zshrc`:
```bash
source $(brew --prefix)/share/zsh-autosuggestions/zsh-autosuggestions.zsh
```

### VS Code Terminal Font Not Displaying
1. Ensure "MesloLGS NF" font is installed: `brew install --cask font-meslo-lg-nerd-font`
2. Restart VS Code
3. Check that `terminal.integrated.fontFamily` is set to "MesloLGS NF"

### Git LFS Not Working
```bash
git lfs install
git lfs pull
```

## Updates

To update Homebrew packages:
```bash
brew update
brew upgrade
```

To update VS Code extensions, click the Extensions icon and check for updates.

To update Oh My Zsh:
```bash
omz update
```

To update Powerlevel10k:
```bash
git -C ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k pull
```
