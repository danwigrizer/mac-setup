# Homebrew

[Homebrew](https://brew.sh/) calls itself _The missing package manager for
macOS_ and is an essential tool for any developer.

## Installation

Before you can run Homebrew you need to have the **Command Line Tools for
Xcode** installed. It include compilers and other tools that will allow you
to build things from source, and if you are missing this it's available
through the App Store > Updates. You can also install it from the terminal
by running the following:

```sh
sudo xcode-select --install
```
Also, make sure to agree to xcode license. If not, run ```sudo xcodebuild -license```

To install Homebrew run the following in a terminal:

```sh
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install.sh)"
```

hit **Enter**, and follow the steps on the screen.

### Setting up your `PATH`

Homebrew suggests running:
- Run these two commands in your terminal to add Homebrew to your PATH:
```sh
echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> /Users/danwigrizer/.zprofile 
eval "$(/opt/homebrew/bin/brew shellenv)" 
```

Then, to be able to use `brew` you need to start a new terminal session. After that
you should make sure everything is working by running:

```sh
brew doctor
```

If everything is good, you should see no warnings, and a message that you are
"ready to brew!".

Sources used:
[1] https://stackoverflow.com/questions/36657321/after-installing-homebrew-i-get-zsh-command-not-found-brew [2]https://www.reddit.com/r/zsh/comments/e882c4/what_is_the_difference_between_zshrc_and_zprofile/
