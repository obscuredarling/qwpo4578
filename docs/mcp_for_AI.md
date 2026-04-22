
RVBuilder provides Model Context Protocol (MCP) servers that enable AI agents to streamline Andes RISC-V project setup, improve configuration accuracy, automate development workflows, or assist in resolving development issues. The level of control available to AI agents depends on how the MCP servers are integrated. As shown below, AI agents such as GitHub Copilot , which directly interact with the MCP server integrated in RVBuilder, provides a higher level of automation across the development workflow. In contrast, AI agents that communicate with the MCP server via standard input/output (STDIO), such as Codex or Claude Code, offer comparatively limited automation and primarily assist with project configuration and development queries.  

| AI Agent | MCP Integration Mode | Capabilities for RVBuilder Projects | Requires VS Code |
|---------|-------------|-------------|-------------|
| GitHub Copilot Chat | Integrated (in RVBuilder extension) |Assistance with project creation/import, configuration, building, debugging, and  development queries | Yes |
| Codex Desktop/CLI | Standalone (STDIO via MCP server) from RVBuilder MCP package |  Assistance with project configuration and development queries | No |
| Claude Code Desktop/CLI | Standalone (STDIO via MCP server) from RVBuilder MCP package |  Assistance with project configuration and development queries | No |

This section outlines the requirements, installation, configuration, and usage of GitHub Copilot, Codex Desktop/CLI, and Claude Code Desktop/CLI for RVBuilder project development. 

## GitHub Copilot Chat 

### Prerequisites
- Visual Studio Code (version 1.9 or later) with the RVBuilder extension installed. For installation instructions of the RVBuilder extension, see [**Install RVBuilder**](./installation.md).
- A GitHub account with an active Copilot subscription or a Copilot free plan

### Installation and Setup
1. In VS Code, click ![Extension](./images/extension.png) in the **Activity Bar**.
2. Search for the **GitHub Copilot Chat** extension and install it. Restart VS Code after the installation. <br> 
 ![GitHub Copilot Chat extension](./images/github_copilot_chat.png)
3. Open the **Chat** view (pressing Ctrl+Alt+I or clicking the **Toggle Chat** icon ![Toggle chat](./images/toggle_chat.png) near the search bar). Follow the prompts to sign in with your GitHub account and authorize VS Code in the browser.  

### Using GitHub Copilot Chat for RVBuilder Development
1. Open the **Chat** view in the VS Code with the RVBuilder extension installed. 
2. Call `@rvbuilder` followed by your request or question for RVbuilder project development. GitHub Copilot supports automation for project creation/import, configuration, building, and debugging. For example, 

    - Request to import a project   
    
       ``@rvbuilder Import a demo from the RVbuilder package to the workspace``

    - Query about the project configuration    
    
       ``@rvbuilder Read the build settings of the project``

    - Request to modify project settings   
    
       ``@rvbuilder Configure the project to improve performance``

    - Request to build and debug the project    
    
       ``@rvbuilder Start debugging and show CPU register values after the program suspends``


## Codex Desktop/CLI 
### Prerequisites
- Codex Desktop or CLI
- Existing RVBuilder project(s) 

### Installation and Setup
1. Download the RVBuilder MCP package `mcp-package.zip` from the
[**RVBuilder MCP**](https://github.com/andestech/RVBuilder/releases/tag/v1.0.0-mcp-package) release page and extract it to a desired directory (e.g. `D:/mcp-package`). The package contains the following components required for Codex to serve as an RVBuilder AI assistant:
    ```
    mcp-package/
     ├── dist/
     │      └── mcp-server.js # Standalone MCP server 
     ├── AGENTS.md            # System prompt for Codex 
     └── resource/
            └── mcp/          # Folder of skill prompts 

    ```

2.  Install `Node.js` (version 1.8 or later) from the official [**Node.js Download**](https://nodejs.org/en/download) page. Verify that both `Node.js` and `npm` are successfully installed and accessible: 

    ``node -v`` <br>
    ``npm -v``
    
3. Install the Codex Desktop app from the [**OpenAI Codex App**](https://openai.com/zh-Hant/codex/) page or install the Codex CLI using: <br>
   ``npm install -g @openai/codex``

### Using Codex for RVBuilder Development
1. Open Codex Desktop or CLI, specify an RVBuilder project (e.g., D:/my-project).
   - In the Codex Desktop app, select the project folder.
   - In the Codex CLI, change the working directory to the project folder. 

2. Copy `AGENTS.md` from the extracted MCP package to the working project directory. For example,<br>
    ``cp D:/mcp-package/AGENTS.md D:/my-project/`` 

3. Configure Codex to use the standalone RVBuilder MCP server by editing the user config `~/.codex/config.toml` and adding a section as follows: 
    ```
    [mcp_servers.rvbuilder]
    command = "node"
    args = ["D:/mcp-package/dist/mcp-server.js"]
    ```

    For Codex Desktop app, you can alternatively configure the MCP server in "Settings > MCP servers". Add an RVBuilder MCP server and set its path to the standalone MCP server in the extracted RVBuilder MCP package. <br> 

    Restart the Codex Desktop app or CLI after the configuration. <br>

4. Use Codex to assist with RVBuilder project development. Codex primarily supports project configuration tasks and provides guidance for development queries.

   - In the Codex Desktop app, enter your request or question in the prompt box.
   - In the Codex CLI, run `codex` followed by your request or requests. For example,<br>
     - ``Codex List the current compiler and linker options for the project.`` 
     - ``Codex Change the compiler from GCC to Clang.``
     


## Claude Code Desktop/CLI 
### Prerequisites
- Claude Code Desktop or CLI
- Existing RVBuilder project(s)

### Installation and Setup
1. Download the RVBuilder MCP package `mcp-package.zip` from the [**RVBuilder MCP**](https://github.com/andestech/RVBuilder/releases/tag/v1.0.0-mcp-package) release page and extract it to a desired directory (e.g., `D:/mcp-package`). The package contains the following components required for Claude Code to serve as an RVBuilder AI assistant:  
    ```
    mcp-package/
     ├── dist/
     │      └── mcp-server.js # Standalone MCP server 
     ├── CLAUDE.md            # System prompt for Claude Code 
     └── resource/
            └── mcp/          # Folder of skill prompts 

    ```

 2. Install `Node.js` (version 1.8 or later) from the official [**Node.js Download**](https://nodejs.org/en/download) page. Verify that both `Node.js` and `npm` are successfully installed and accessible: 

    ``node -v`` <br>
    ``npm -v``

3. Install the Claude Code globally. 

   ``npm install -g @anthropic-ai/claude-code`` 
    
    To use the Claude Code Desktop app, download and install it from the [**Claude Download**](https://claude.ai/downloads) page then.

### Using Claude Code for RVBuilder Development

1. Open Claude Code Desktop or CLI, specify an RVBuilder project (e.g., D:/my-project).
   - In the Claude Code Desktop app, select the project folder.
   - In the Claude Code CLI, change the working directory to the project folder. 

2. Copy `CLAUDE.md` from the extracted MCP package to the working project directory. For example,<br>
    ``copy D:/mcp-package/CLAUDE.md D:/my-project/`` 

3. Register the standalone MCP server in the extracted RVBuilder MCP package for the project.<br>
    ``claude mcp add -s local rvbuilder node "D:/mcp-package/dist/mcp-server.js"``

4. Use Claude Code to assist with your RVBuilder development. Claude Code primarily supports project configuration tasks and provides guidance for development queries.

   - In the Claude Code Desktop app, enter your request or question in the prompt box.
   - In the Claude Code CLI, run `claude` followed by your request or requests. For example,<br>
     - ``Claude Change the project target to ADP-AE350-A45 and update build settings`` <br>
     - ``Claude Enable DSP for my project``
     - ``Claude What are the issues that might cause build failures?``

