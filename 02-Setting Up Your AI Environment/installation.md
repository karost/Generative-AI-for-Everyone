### INSTALL SOFTWARE for Generative Tools OUTPUT: [TEXT , IMAGE , VOICE , VIDEO ], INPUT: [ AI CHAT , AI CODE ASSISTANT, AI SEARCH ENGINE, MCP SERVER ]

<img src="https://github.com/nvm-sh/logos/blob/main/nvm-logo-color-avatar-white.png" width="60">


1. Node Version Manager (NVM)
https://github.com/nvm-sh/nvm?tab=readme-ov-file#install--update-script

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


<img src="https://www.anaconda.com/wp-content/uploads/2024/11/2020_Anaconda_Logo_RGB_Corporate.png" width="150"> 

3. Python Environment Manager ( VENV, Mini Conda )
```
# Downlaod and install Miniconda

https://www.anaconda.com/docs/getting-started/miniconda/install#using-miniconda-in-a-commercial-setting
# mac-intel last version support
curl -O https://repo.anaconda.com/miniconda/Miniconda3-py39_25.7.0-2-MacOSX-x86_64.sh

# mac-arm 
curl -Ohttps://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh

# bash ~/Miniconda3-py39_25.7.0-2-MacOSX-x86_64.sh
```

<img src="https://git-scm.com/images/logo@2x.png" width="90">

4. Git
```
https://git-scm.com/downloads
```


5. VS Code + Extension, Git

```
https://code.visualstudio.com/download
```

6. Cloud LLM API Key (OpenAI, anthropic, DeepSeek ) export API_KEY to console environment

7. AI Coding Assistants and AI Tools
- CLI-based AI coding assistants ( Aider, Cusor, VS Code extension [CLINE]
- Agentic CLI-coding assistants ( agentic CLI ):  Claude Code, Gemini CLI , Qwen CLI )

8. No-code/Low-code AI workflow automation tools ( n8n, flowise )


9. MCP Server Tools


10. Version Tools (AI generate video , voice , image )




