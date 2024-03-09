# new_mac_setup
Reminders to run on a new Mac running osx on apple silicon


Mostly follow [Rami Krispin's awesome-ds-setting repo](https://github.com/RamiKrispin/awesome-ds-setting) but instead of conda I'm using poetry and pyenv, which requires a little extra work.

# Preamble: Homebrew, git, and iterm

Very first thing is to run `git` so we can start downloading apple dev tools. Once that's done, we can start with everything else.

* See [Rami Krispin's awesome-ds-setting repo](https://github.com/RamiKrispin/awesome-ds-setting) first few steps

## Brew

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then: 
```bash
brew install iterm2
brew install xz     # Helps to install pyenv/poetry later

brew install graphviz  # Needed to make directed graphs with pygraphviz
```

## Poetry

See [this gist](https://gist.github.com/banditkings/f00813d95dce905638d88dbae8f810fe) for a Poetry checklist

## Pyenv

From [pyenv homebrew installation instructions:](https://github.com/pyenv/pyenv?tab=readme-ov-file#homebrew-in-macos):

```bash
brew update
brew install pyenv
```

Then install a new version of python and make it global i.e. 

```bash
pyenv install 3.10.12
# make it global
pyenv global 3.10.12
```

## Quarto and TinyTex

Download the CLI from [Quarto](https://quarto.org/docs/get-started/) and install for all users

Open a new terminal and install tinytex:

```bash
quarto install tinytex
```

Add the VSCode extension as needed. Next we'll need to figure out how to make Quarto play nice with pyenv. You may need to set the `QUARTO_PYTHON` environment variable to point to your .pyenv shims, typically located in `/Users/youruserid/.pyenv/shims/python`, which you'd need to add to your `.zshrc` file as a new line:

```bash
export QUARTO_PYTHON=/Users/youruserid/.pyenv/shims/python
```

and substituting your user id, of course.
```


