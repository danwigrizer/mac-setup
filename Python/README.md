# Python

macOS, like Linux, ships with [Python](https://python.org/) already installed.
But you don't want to mess with the system Python (some system tools rely on
it, etc.), so we'll install our own version(s). 

# Installation - Pyenv method


Installing and configuring pyenv is the first step in our Python setup journey. pyenv is really the cornerstone of my Python setup.

We will install [pyenv](https://github.com/pyenv/pyenv) to maintain sanity while managing multiple Python versions and environments. pyenv was heavily inspired by `rbenv` (for Ruby), and in many ways is similar to `nvm` (for Node.js) as well.

At a high level, `pyenv` first intercepts Python commands using [`shim` executables](https://en.wikipedia.org/wiki/Shim_(computing)) that are injected into `PATH`; it then determines which Python version has been specified; and finally it passes your commands along to the correct Python installation.

Besides the official docs, the best guide to pyenv I could find is [this one by the folks at RealPython](https://realpython.com/intro-to-pyenv/).

## Install the dependencies in advance

```sh
# https://github.com/pyenv/pyenv/wiki#suggested-build-environment
brew update && brew install readline sqlite3 xz zlib openssl
```

*openssl*

[OpenSSL](https://www.openssl.org) is a dependency for several `brew` formulae, but given that Apple has `LibreSSL` by default on macOS Catalina, let's install `openssl` ourselves:

few caveats regarding `openssl`:

> `openssl@1.1`: A CA file has been bootstrapped using certificates from the system keychain. To add additional certificates, place `.pem` files in `/opt/homebrew/etc/openssl@3/certs` and run
`/opt/homebrew/opt/openssl@3/bin/c_rehash`.
`openssl@3` is keg-only, which means it was not symlinked into `/opt/homebrew`, because macOS provides LibreSSL.
> 
> If you need to have `openssl@3` first in your `PATH` run: `echo 'export PATH="/opt/homebrew/opt/openssl@3/bin:$PATH"' >> ~/.zshrc`
> 
> For compilers to find `openssl@1.1` you may need to set:
> ```zsh
>  export LDFLAGS="-L/opt/homebrew/opt/openssl@1.1/lib"
>  export CPPFLAGS="-I/opt/homebrew/opt/openssl@1.1/include"
> ```

Caveats regarding `readline`:

> `readline` is keg-only, which means it was not symlinked into `/opt/homebrew`, because macOS provides BSD `libedit`.
>
> For compilers to find `readline` you may need to set:
> ```zsh
>  export LDFLAGS="-L/opt/homebrew/opt/readline/lib"
>  export CPPFLAGS="-I/opt/homebrew/opt/readline/include"
> ```

Caveats regarding `sqlite`:

> `sqlite` is keg-only, which means it was not symlinked into `/opt/homebrew`, because macOS already provides this software and installing another version in parallel can cause all kinds of trouble.
>
> If you need to have `sqlite` first in your `PATH` run: `echo 'export PATH="/opt/homebrew/opt/sqlite/bin:$PATH"' >> ~/.zshrc`
>
> For compilers to find `sqlite` you may need to set:
> ```zsh
>  export LDFLAGS="-L/opt/homebrew/opt/sqlite/lib"
>  export CPPFLAGS="-I/opt/homebrew/opt/sqlite/include"
> ```
> For `pkg-config` to find `sqlite` you may need to set:
> ```zsh
>  export PKG_CONFIG_PATH="/usr/local/opt/sqlite/lib/pkgconfig"
> ```

Caveats regarding `zlib`:

> `zlib` is keg-only, which means it was not symlinked into `/opt/homebrew`, because macOS already provides this software and installing another version in parallel can cause all kinds of trouble.
> 
> For compilers to find `zlib` you may need to set:
> ```zsh
>  export LDFLAGS="-L/opt/homebrew/opt/zlib/lib"
>  export CPPFLAGS="-I/opt/homebrew/opt/zlib/include"
> ```
>
> For `pkg-config` to find `zlib` you may need to set:
> ```zsh
>  export PKG_CONFIG_PATH="/opt/homebrew/opt/zlib/lib/pkgconfig"
> ```



First, we must install `pyenv` using Homebrew:

```sh
brew install pyenv
```

To upgrade `pyenv` in the future, use `upgrade` instead of `install`. 

After installing, add `pyenv init` to your shell to enable shims and autocompletion:

```sh
echo 'eval "$(pyenv init --path)"' >> ~/.zprofile

echo 'eval "$(pyenv init -)"' >> ~/.zshrc

```

Restart your shell to make sure the path changes take effect.

```sh
exec $SHELL
```
Source:
https://laict.medium.com/install-python-on-macos-11-m1-apple-silicon-using-pyenv-12e0729427a9
[2] https://github.com/pyenv/pyenv/wiki#suggested-build-environment

pyenv suggests that before install any version of Python, we need a Python build environment for Mac. Make sure you have Xcode Command Line Tools ( xcode-select --install) and Homebrew on your system. Then:

```sh
brew install openssl readline sqlite3 xz zlib
```

You can now begin using `pyenv`. To list the all available versions of Python,
including Anaconda, Jython, PyPy and Stackless, use:

```sh
pyenv install --list
```

Then install the desired versions:

```sh
pyenv install 3.10.0
```

Use the `global` command to set global version(s) of Python to be used in all
shells. For example, if you prefer 2.7.12 over 3.5.2:

```sh
pyenv global 3.10.0
pyenv rehash
```

The leading version takes priority. All installed Python versions can be
located in `~/.pyenv/versions`. Alternatively, you can run:

```console
> pyenv versions
  system
* 3.10.0 (set by /Users/danwigrizer/.pyenv/version)
```

This shows an asterisk `*` next to the currently active version.

## Keep pyenv updated

In order to use the latest Python (and miniconda) versions, we will need to upgrade pyenv regularly:

```sh
brew update && brew upgrade pyenv
```

For the list of versions that are included in each release of pyenv, check out [the official repository](https://github.com/pyenv/pyenv/releases).

### Application-specific Python version

The `local` command will set local application-specific Python version(s) by
writing the version name to a `.python-version` file in the current directory.
This version overrides the global version. For example, to install
anaconda3-4.1.1 in `path/to/directory`:

```console
$ pyenv install anaconda3-4.1.1
$ cd path/to/directory
$ pyenv local anaconda3-4.1.1
$ pyenv rehash
$ pyenv versions
  system
  2.7.12
  3.5.2
* anaconda3-4.1.1 (set by /Users/your_account/path/to/directory/.python-version)
```

Sources:
https://lucasrla.github.io/python-on-macos/pyenv/pyenv.html

