
Now you should install a framework, we recommend to use [Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh)


The configuration file for `zsh` is called `.zshrc` and lives in your home
folder (`~/.zshrc`).

## Oh My Zsh

[Oh My Zsh](https://github.com/robbyrussell/oh-my-zsh) is an open source,
community-driven framework for managing your `zsh` configuration. It comes
with a bunch of features out of the box and improves your terminal experience.

Install Oh My Zsh:

```sh
sh -c "$(curl -fsSL https://raw.githubusercontent.com/robbyrussell/oh-my-zsh/master/tools/install.sh)"
```

## powerlevel10k

- Download [powerlevel10k](https://github.com/romkatv/powerlevel10k#instant-prompt)
- Clone the repository:
```sh
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

- Set ZSH_THEME="powerlevel10k/powerlevel10k" in ~/.zshrc.
- p10k configure can install the recommended font for you. Simply answer Yes when asked whether to install Meslo Nerd Font.

### Configuration

The out-of-the-box configuration is usable but you probably want to customise
it to suit your needs. The [Official Wiki](https://github.com/robbyrussell/oh-my-zsh/wiki)
contains a lot of useful information if you want to deep dive into what you
can do with Oh My Zsh, but we'll cover the basics here.

To apply the changes you make you need to either **start new shell instance**
or run:

```sh
source ~/.zshrc
```

#### Plugins

Add plugins to your shell by adding the name of the plugin to the `plugin`
array in your `.zshrc`.

```sh
plugins=(git colored-man-pages colorize pip python brew osx)
```

You'll find a list of all plugins on the [Oh My Zsh Wiki](https://github.com/robbyrussell/oh-my-zsh/wiki/Plugins).
Note that adding plugins can cause your shell startup time to increase.

##### zsh-syntax-highlighting

The Syntax Highlighting plugin adds beautiful colors to the commands you are typing.

Clone the zsh-syntax-highlighting plugin’s repo and copy it to the “Oh My ZSH” plugins directory.

```sh
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-syntax-highlighting
```

##### zsh-autosuggestions

This plugin auto suggests any of the previous commands. Pretty handy! To select the completion, simply press → key.

Clone the zsh-autosuggestions plugin’s repo and copy it to the “Oh My ZSH” plugins directory.

```sh
git clone https://github.com/zsh-users/zsh-autosuggestions $ZSH_CUSTOM/plugins/zsh-autosuggestions
```


## Other plugins added

1. pip
2. python

plugins=(git zsh-autosuggestions zsh-syntax-highlighting pip python)

##### Enforce Changes

To apply the changes you make you need to either **start new shell instance**
or run:

```sh
source ~/.zshrc
```

## `env.sh`

To include `env.sh`, open `~/.zshrc` and add the following:

```sh
source ~/<path to file>/env.sh
```

This file comes with some pre-defined settings, **they are all optional**.
Please review them before you use them as your configuration. These are just
examples to show you what you can customise in your shell.

```sh
#!/bin/zsh

# Add commonly used folders to $PATH
export PATH="/usr/local/bin:/usr/bin:/bin:/usr/sbin:/sbin"

# Specify default editor. Possible values: vim, nano, ed etc.
export EDITOR=vim

# File search functions
function f() { find . -iname "*$1*" ${@:2} }
function r() { grep "$1" ${@:2} -R . }

# Create a folder and move into it in one command
function mkcd() { mkdir -p "$@" && cd "$_"; }

# Example aliases
alias cppcompile='c++ -std=c++11 -stdlib=libc++'
alias g='git'
```
