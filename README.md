# dotfiles for my wsl and linux environments
1. zsh & oh-my-zsh
2. tools : git powershell docker 
3. development : go node

https://wilsonmar.github.io/zsh/

https://sourabhbajaj.com/mac-setup/iTerm/fzf.html

https://dev.to/snaka/10-things-i-always-setup-in-git-when-i-prepare-a-new-environment-d99



# mac setup

1. Install Homebrew

   ```shell
   xcode-select --install

   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"

   ```

1. install zsh and zsh-completions

   ```
   brew install zsh zsh-completions
   ```

1. Install iterm2

   a. Restore iterm2 settings

1. Install Nerd Fonts

   ```shell
   brew tap homebrew/cask-fonts
   brew install font-fira-code --cask
   ```

1. Install Starship.sh prompt

   ```shell
   brew install starship

   #install at end of ~/.zshrc
   eval "$(starship init zsh)"
   ```

1. brew install tools and applications

   ```shell
   # macos utilities
   brew install raycast \
      finicky \
      drawio  \

   # cli tools
   brew install \
    jq \
    exa \
    bat \
    tree \

   ```

1. install scripts

   ```shell
   # aws-cli
   cd ~ && mkdir -p ~/install && cd ~/install
   curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
   sudo installer -pkg AWSCLIV2.pkg -target /
   rm AWSCLIV2.pkg
   cd ~ && rmdir ~/install
   ```

1. Install from the Apple Appstore

   a. Tampermonkey

   b. Magnet

1. Restore configuration

   a. zshrc
         
         ```
         cd $HOME
         
         cat << 'EOF' > .zshrc

         # zsh options
         setopt GLOB_COMPLETE
         setopt AUTO_CD
         export SAVEHIST=5000
         export HISTSIZE=2000
         setopt EXTENDED_HISTORY
         setopt SHARE_HISTORY
         setopt APPEND_HISTORY
         setopt INC_APPEND_HISTORY
         setopt HIST_EXPIRE_DUPS_FIRST
         setopt HIST_IGNORE_DUPS
         setopt HIST_FIND_NO_DUPS
         setopt HIST_REDUCE_BLANKS
         setopt CORRECT
         setopt CORRECT_ALL

         # Use GNU dircolors for ls -- specific to MacOS
         PATH="/usr/local/opt/coreutils/libexec/gnubin:$PATH"
         MANPATH="/usr/local/opt/coreutils/libexec/gnuman:$MANPATH"

         export LANG=en_US.UTF-8

         if type brew &>/dev/null; then
           FPATH=$(brew --prefix)/share/zsh-completions:$FPATH

           autoload -Uz compinit
           compinit
         fi

         if [ "$(command -v exa)" ]; then
            unalias -m 'll'
            unalias -m 'l'
            unalias -m 'la'
            unalias -m 'ls'
            alias ls='exa -G --color auto -s type'
            alias ll='exa -lh --color auto -s type'
            alias la='exa -lh --color auto -a -s type'
         fi

         if [ "$(command -v bat)" ]; then
            unalias -m 'cat'
            alias cat='bat -pp --theme="Nord"'
         fi

         # Must be at end of file
         eval "$(starship init zsh)"
         EOF
         ```

   a. starship.toml

         
         ```
         mkdir -p ~/.config && cd ~/.config
         
         cat << 'EOF' > starship.toml
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
         format = 'via [${symbol}${pyenv_prefix}(${version} )(\($virtualenv\) )]($style)'
         pyenv_version_name = true
         EOF
         ```

