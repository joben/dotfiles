# dotfiles for my wsl and linux environments
1. zsh & oh-my-zsh
2. tools : git powershell docker 
3. development : go node


# mac setup

1. Install Homebrew

```shell
xcode-select --install

/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

```
2. Install iterm2
a. Restore iterm2 settings

3. Install Nerd Fonts

```shell
brew tap homebrew/cask-fonts
brew install font-fira-code --cask
```
4. Install Starship.sh prompt

```shell
brew install starship

#install at end of ~/.zshrc
eval "$(starship init zsh)"

```

5. Restore configuration
a. starship

```shell
mkdir -p ~/.config && cd ~/.config
cat << EOF > starship.toml
add_newline = false

[cmd_duration]
min_time = 500
format = "[$duration](bold yellow)"

[character]
success_symbol = "→"
format = "$symbol "

[aws]
style = "bold orange"
format = "on [$symbol($profile )\($region\)(\[$duration\]) ]($style)"

[aws.region_aliases]
ap-southeast-1 = "SG"
us-east-1 = "VA"

[python]
symbol = "🐍 "
format = "via [${sumbol}${pyenv_prefix}(${version} )(\($virtualenv\))]($style)"
pyenv_version_name = true





```

