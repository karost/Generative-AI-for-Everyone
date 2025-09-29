### 1.Install MCP Server in local macine as global 
- chadcn/ui MCP office version : https://ui.shadcn.com/docs/mcp
```
npx shadcn@latest mcp init

npx shadcn@latest mcp init --client claude

```


### 2.Setting MCP Server Config

```
npx shadcn@latest mcp init
✔ Which MCP client are you using? › VS Code
✔ Configuring MCP server.
✔ Installing dependencies.

Configuration saved to .vscode/mcp.json. :

{
  "servers": {
    "shadcn": {
      "command": "npx",
      "args": [
        "shadcn@latest",
        "mcp"
      ]
    }
  }
}

```
Playwight:

```
{
  "mcpServers": {
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest"
      ]
    }
  }
}
```
---
### Kilo-code MCP Setting

```
{
  "mcpServers": {
    "shadcn": {
      "command": "npx",
      "args": [
        "shadcn@latest",
        "mcp"
      ]
    },
    "playwright": {
      "command": "npx",
      "args": [
        "@playwright/mcp@latest"
      ],
      "disabled": false,
      "alwaysAllow": []
    }
  }
}
```
