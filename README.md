# Iterm2 with ZSH

(My Windows 10 Setup with [ConEmu](https://conemu.github.io/) is not included. I might do it in the future.)

---

# Why

This repository is how I backup my own configuration. And while doing so, why not share it and save you some time in case you like my setup.

# Tools

- [iTerm2](https://iterm2.com/)
  - Why?
    - Native macOS terminal is very limited and hard to configure.
    - Comes with integrated [tmux](https://github.com/tmux/tmux/wiki) for awesome window management
- [ZSH](https://ohmyz.sh)
  - Why
    - Higly popular, a lot of community built plugins for improved productivity

# Setup

- Download and install [iTerm2](https://iterm2.com/)
  - You can also easily install it using [brew](https://formulae.brew.sh/cask/iterm2)
  - brew install --cask iterm2
- Download the [agjs-iterm2-profile.json](./assets/settings/agjs-iterm2-profile.json)
- Open your iterm2 and import the JSON.
  - _Preferences > Profiles > Other Actions... > Import JSON Profiles..._

Once done, your iterm2 will obviously inherit all of my own settings. This also includes shortcuts.

# ZSH Theme - [powerlevel10k](https://github.com/romkatv/powerlevel10k#oh-my-zsh)

You can either follow the instructions here or directly on the provided link above.

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

- This will install the specified theme into the custom themes directory. This is where all the custom ZSH themes reside.

Once the theme is cloned, we'll have to change our .zshrc file.

```bash
vi ~/.zshrc
```

Find the _ZSH_THEME_ and set it to powerlevel10k/powerlevel10k.

```bash
ZSH_THEME="powerlevel10k/powerlevel10k"
```

Quit vim and source the _~/.zshrc_ so changes are propagated.

```bash
source ~/.zshrc
```

At this point, you have two choices. Either use the provided _~/.p10k.zsh_ file I've included in this repo or configure the theme on your own. The mentioned file defines all the configuration for the previously installed theme.

If you decide to include my own file, don't worry. You can always reconfigure it by running:

```bash
p10k configure
```

## Using my own p10k.zsh configuration file

- Download the [.p10k.zsh](./assets/settings/.p10k.zsh)
- Put it inside _~/.p10k.zsh_ (your $HOME directory, ls -a $HOME)
- Completely quit and reopen iTerm2

## Fresh

- Completely quit and reopen iTerm2
- Go through the configuration wizard invoked by p10k

# Shortcuts

- Open/Close iTerm2: **SHIFT + CMD + 1**

# Git

https://github.com/woefe/git-prompt.zsh#examples
https://github.com/dandavison/delta

## Aliases

- alias.st=status -sb
- alias.lg=log --oneline
- alias.last=log -1 HEAD --stat
- alias.gl=config --global -l
- alias.se=!git rev-list --all | xargs git grep -F
- core.pager=delta
