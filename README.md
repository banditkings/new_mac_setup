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

Add the VSCode extension as needed. 

### Quarto within a poetry+pyenv virtual environment

Quarto has a few issues with a poetry/pyenv environment. There aren't any issues with running an interactive session within VSCode because it asks you to specify the jupyter kernel, you're asked to specify the kernel when running an interactive session and it should be able to detect the right one. 

**However**, the problems start once we try to `quarto preview` or `quarto render`. Here I'll talk about the differnt things you can try. A lot of this stems from where your jupyter kernel lives and whether you manage it within a poetry environment.

The key seems to be the `QUARTO_PYTHON` environment variable. You can get it to point to your .pyenv shims, typically located in `/Users/youruserid/.pyenv/shims/python`, which you'd need to add to your `.zshrc` file as a new line:

```bash
export QUARTO_PYTHON=/Users/youruserid/.pyenv/shims/python
```
and substituting your user id, of course. If you're simply using `pyenv` then this should be sufficient.

However, if you're working within a `poetry` environment, you'll need to set `QUARTO_PYTHON` to the poetry virtual environment, which will be in a directory full of random letters and numbers like `/Users/youruserid/Library/Caches/pypoetry/virtualenvs/quarto-book-5nMdc-E9-py3.10/bin/python`.

So you could theoretically temporarilily set the `QUARTO_PYTHON` environment variable to this poetry virtual env just before you run the `quarto render` command but this seems suboptimal. Ideally there would be some config file that we can mess with. I need to research this further, 

* Right now, I'm thinking that we need to expose the `poetry` kernel to the `pyenv` version. For example, I have jupyter installed in a `pyenv` envrionment using python 3.10.12, and `poetry` envrionment also using python 3.10.12. If I can link the kernel from one to another then that should be bueno, yes?


