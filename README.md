# Iterm2 with ZSH

(My Windows 10 Setup with [ConEmu](https://conemu.github.io/) is not included. I might do it in the future.)

---

## Why

This repository is how I backup my own configuration. And while doing so, why not share it and save you some time in case you like my setup.

## Tools

- [iTerm2](https://iterm2.com/)
  - Why?
    - Native macOS terminal is very limited and hard to configure
    - Comes with integrated [tmux](https://github.com/tmux/tmux/wiki) for awesome window management
- [ZSH](https://ohmyz.sh)
  - Why
    - Higly popular, a lot of community built plugins for improved productivity

## Setup

- Download and install [iTerm2](https://iterm2.com/)
  - You can also easily install it using [brew](https://formulae.brew.sh/cask/iterm2)
  - brew install --cask iterm2
- Download the [agjs-iterm2-profile.json](./assets/settings/agjs-iterm2-profile.json)
- Open your iterm2 and import the JSON.
  - _Preferences > Profiles > Other Actions... > Import JSON Profiles..._

Once done, your iterm2 will obviously inherit all of my own settings. This also includes shortcuts.

---

### ZSH Theme - [powerlevel10k](https://github.com/romkatv/powerlevel10k#oh-my-zsh)

You can either follow the instructions here or directly on the provided link above.

```bash
git clone --depth=1 https://github.com/romkatv/powerlevel10k.git ${ZSH_CUSTOM:-$HOME/.oh-my-zsh/custom}/themes/powerlevel10k
```

- This will install the specified theme into the custom themes directory. This is where all the custom ZSH themes reside.

Once the theme is cloned, we'll have to change our _.zshrc_ file. In case you are unfamiliar with _.zshrc_, this is the main configuration file where ZSH defines all its settings.

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

### Using my own p10k.zsh configuration file

- Download the [.p10k.zsh](./assets/settings/.p10k.zsh)
- Put it inside _~/.p10k.zsh_ (your $HOME directory, ls -a $HOME)
- Completely quit and reopen iTerm2

#### Fresh

- Completely quit and reopen iTerm2
- Go through the configuration wizard invoked by p10k. The wizard will be automatically shown in your terminal as that will be the first session running using previously installed theme. In case you mess up and you don't like the choices you made, as I previously said, simply run _p10k configure_ and run through the wizard again.

---

### iTerm2 Shortcuts

- Open/Close iTerm2: **SHIFT + CMD + 1**
- Open New Window: **CMD + N**
- Vertial Split: **CMD + D**

---

## Git

https://github.com/woefe/git-prompt.zsh#examples

### Aliases

#### Better _git diff_

Native git diff is pretty horrendous. It's incredibly difficult to read. Due to that, I'm using [Delta](https://github.com/dandavison/delta).

```bash
brew install git-delta
```

We have to tell our Git to use a different [pager](https://git-scm.com/book/en/v2/Customizing-Git-Git-Configuration#_core_pager). Pager is essentially a function that formats the output of a git log and git diff commands.

```bash
# sets delta as the default pager
git config --global core.pager delta
```

Once setup, give it a shot. Try some _git diff_, _git show_ and see if you like the output. If you don't like the output and you would like the old one back, simply set the pager to the default one

```bash
# sets delta to the default pager, which is less
git config --global core.pager less
```

For more configuration options, make sure to read this awesome article I found at [dev.to](https://dev.to/cloudx/delta-a-new-git-diff-tool-to-rock-your-productivity-2773). All credit to the [author](https://dev.to/navarroaxel).

- alias.st=status -sb
- alias.lg=log --oneline
- alias.last=log -1 HEAD --stat
- alias.gl=config --global -l
- alias.se=!git rev-list --all | xargs git grep -F
- core.pager=delta
