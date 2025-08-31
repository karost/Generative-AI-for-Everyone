### INSTALL SOFTWARE for Generative Tools OUTPUT: [TEXT , IMAGE , VOICE , VIDEO ], INPUT: [ AI CHAT , AI CODE ASSISTANT, AI SEARCH ENGINE, MCP SERVER ]

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
Downlaod and install Miniconda

- Link to Download:[Miniconda ](https://www.anaconda.com/docs/getting-started/miniconda/install#using-miniconda-in-a-commercial-setting)
```
# mac-intel last version support
curl -O https://repo.anaconda.com/miniconda/Miniconda3-py39_25.7.0-2-MacOSX-x86_64.sh

# mac-arm 
curl -Ohttps://repo.anaconda.com/miniconda/Miniconda3-latest-MacOSX-arm64.sh

# bash ~/Miniconda3-py39_25.7.0-2-MacOSX-x86_64.sh
```

<img src="https://git-scm.com/images/logo@2x.png" width="90">

4. Git
   
- Link to Download:[Git Link](https://git-scm.com/downloads)


<img src="https://github.com/karost/Generative-AI-for-Everyone/blob/main/images/icons/microsoft_visual_studio_code_macos_bigsur_icon_189957.png" width="100">

5. VS Code + Extension, Git

- Link to Download:[VS CODE ](https://code.visualstudio.com/download)


6. Cloud LLM API Key (OpenAI, anthropic, DeepSeek ) export API_KEY to console environment
Link to Download:      
- [OpenAi Platfrom ](https://platform.openai.com/api-keys).

- [Anthropic Platfrom](https://console.anthropic.com/login?returnTo=%2F%3F).

- [DeepSeek Platfrom](https://platform.deepseek.com/sign_in).

- [Google Free API KEY](https://aistudio.google.com/apikey).




7. AI Coding Assistants and AI Tools
- CLI-based AI coding assistants ( Aider, Cusor, VS Code extension [CLINE]
- Agentic CLI-coding assistants ( agentic CLI ):  Claude Code, Gemini CLI , Qwen CLI )

8. No-code/Low-code AI workflow automation tools ( n8n, flowise )

- Start make self host: [Self Host for n8n](https://docs.n8n.io/hosting/installation/npm/).

9. MCP Server Tools

<img src="https://github.com/karost/Generative-AI-for-Everyone/blob/main/images/icons/claude-color.svg" width="50">

- Link to Download:[Claude Desktop](https://claude.ai/download).



10. Version Tools (AI generate video , voice , image )




