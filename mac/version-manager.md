```shell

brew install asdf

echo -e "\n. $(brew --prefix asdf)/libexec/asdf.sh" >> ${ZDOTDIR:-~}/.zshrc

# nodejs

brew install gpg gawk

asdf plugin add nodejs https://github.com/asdf-vm/asdf-nodejs.git
asdf install nodejs latest

# python
brew install openssl readline sqlite3 xz zlib tcl-tk
asdf plugin add python https://github.com/danhper/asdf-python.git
asdf list all python
asdf install python 3.9.14

# use direnv integration with asdf
asdf plugin add direnv
asdf direnv setup --shell zsh --version system

```
