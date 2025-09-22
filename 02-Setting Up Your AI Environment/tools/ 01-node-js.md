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
for windows 11

https://github.com/coreybutler/nvm-windows

---
<img src="https://upload.wikimedia.org/wikipedia/commons/d/d9/Node.js_logo.svg" width="100">
2. Check NVM Version and Install Node.js with a specific version
current information, Node.js v22 is the active LTS version, v24 will active LTS 2025

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

// install the latest stable version of Node
nvm install stable

```
---

