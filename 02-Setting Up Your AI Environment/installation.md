### INSTALL SOFTWARE

1. Node Version Manager (NVM)
https://github.com/nvm-sh/nvm?tab=readme-ov-file#install--update-script

current information, Node.js v22 is the active LTS version , v24 will active LTS at 2025

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



```sh
// Check version
nvm -v

node -v 

// list locally installed versions of node
nvm ls

// list remote available versions of node
nvm ls-remote

// install specific version of node
nvm install 18.16.1

// set default version of node
nvm alias default 18.16.1

// switch version of node
nvm use 20.5.1

// install latest LTS version of node (Long Term Support)
nvm install --lts

// install latest stable version of node
nvm install stable

```
