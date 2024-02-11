# new_mac_setup
Reminders to run on a new Mac running osx on apple silicon

* Reference: [Rami Krispin's awesome-ds-setting repo](https://github.com/RamiKrispin/awesome-ds-setting)

# Preamble: Homebrew, git, and iterm

Very first thing is to run `git` so we can start downloading apple dev tools. Once that's done, we can start with everything else.

* See [https://github.com/RamiKrispin/awesome-ds-setting] first few steps

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
