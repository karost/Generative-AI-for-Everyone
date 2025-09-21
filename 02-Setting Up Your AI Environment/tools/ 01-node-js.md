### INSTALL SOFTWARE for Generative Tools 

<img src="https://github.com/nvm-sh/logos/blob/main/nvm-logo-color-avatar-white.png" width="60">
1. Node Version Manager (NVM)
[Node Version Manager ](https://github.com/nvm-sh/nvm)

```

// Download and Install
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash

// Edit profile
vi ~/.zshrc

export NVM_DIR="$([ -z "${XDG_CONFIG_HOME-}" ] && printf %s "${HOME}/.nvm" || printf %s "${XDG_CONFIG_HOME}/nvm")"
[ -s "$NVM_DIR/nvm.sh" ] && \. "$NVM_DIR/nvm.sh" # This loads nvm

// Reload profile
source ~/.zshrc

```
---

