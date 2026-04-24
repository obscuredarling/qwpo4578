RVBuilder provides Model Context Protocol (MCP) servers that enable AI agents to streamline Andes RISC-V project setup, improve configuration accuracy, automate development workflows, and assist in resolving development issues.

These MCP servers expose a set of resource primitives, as shown below, that supply domain-specific reference knowledge for AI-assisted RVBuilder workflows. When handling requests or queries related to compiler options, linker scripts, debugger commands, or general RVBuilder project configuration, these resources provide the necessary context to generate accurate and relevant responses.

| Resource | Domain Knowledge / Reference |
|----------|------------------------------|
| `rvbuilder-json` | Target and connection settings |
| `rvbuilder-examples` | Practical workflow examples |
| `gcc-riscv` | GCC/G++ compiler options for RISC-V and Andes extensions |
| `clang-riscv` | LLVM Clang compiler options for RISC-V |
| `gnu-ld-riscv` | GNU Linker (ld) options, linker scripts, relaxation |
| `binutils-riscv` | GNU Binutils (as, ar, objdump, objcopy, readelf, nm, size) |
| `gdb-riscv` | GDB debugger commands |
| `openocd-riscv` | OpenOCD/ICEman debug server setup and JTAG configuration |

The level of control available to AI agents depends on how the MCP servers are integrated. As shown below, AI agents such as GitHub Copilot, which directly interact with the MCP server integrated in RVBuilder, provides a higher level of automation across development workflow. In contrast, AI agents that communicate with the MCP server via standard input/output (STDIO), such as Codex or Claude Code, offer comparatively limited automation and primarily assist with project configuration and development queries.  

| AI Agent | MCP Integration Mode | Capabilities for RVBuilder Projects | Requires VS Code |
|----------|----------------------|-------------------------------------|------------------|
| GitHub Copilot Chat | Integrated (in RVBuilder extension) |Assistance with project creation/import, configuration, building, debugging, and  development queries | Yes |
| Codex Desktop/CLI | Standalone (STDIO via MCP server) |  Assistance with project configuration and development queries | No |
| Claude Code Desktop/CLI | Standalone (STDIO via MCP server) |  Assistance with project configuration and development queries | No |

This section outlines the requirements, installation, configuration, and usage of GitHub Copilot, Codex Desktop/CLI, and Claude Code Desktop/CLI for RVBuilder project development. Note that while RVBuilder workflows support both Linux and Windows environments, the  instructions below use Windows and PowerShell as examples.

## GitHub Copilot Chat 

### Requirements
- Visual Studio Code (version 1.116 or later) with the RVBuilder extension installed. For installation instructions of the RVBuilder extension, see [**Install RVBuilder**](./installation.md).
- GitHub Copilot Chat extension (version 0.41 or later)
- A GitHub account with an active Copilot subscription or a Copilot Free plan. 

### Installation and Setup
1. In VS Code, click ![Extension](./images/extension.png) in the **Activity Bar**.
2. Search for the **GitHub Copilot Chat** extension and install it. Restart VS Code after the installation. <br> 
 ![GitHub Copilot Chat extension](./images/github_copilot_chat.png)
3. Open the **Chat** view (pressing Ctrl+Alt+I or clicking the **Toggle Chat** icon ![Toggle chat](./images/toggle_chat.png) near the search bar). Follow the prompts to sign in with your GitHub account and authorize VS Code in the browser.  

### RVBuilder Development with GitHub Copilot Chat
1. Open the **Chat** view in the VS Code with the RVBuilder extension installed. 
2. Call `@rvbuilder` followed by your request or question for RVbuilder project development. GitHub Copilot supports automation for project creation/import, configuration, building, and debugging. For example, 

    - Request to import a project   
       ``@rvbuilder Import a demo from the RVbuilder package to the workspace``

    - Query about project configuration    
        ``@rvbuilder Read the build settings of the project``

    - Request to modify project settings   
        ``@rvbuilder Configure the project to improve performance``

    - Request to build and debug the project    
        ``@rvbuilder Start debugging and show CPU register values after the program suspends``


## Codex Desktop/CLI 
### Requirements
- Codex Desktop (version 26.421.11020 or later) or Codex CLI (version 0.122.0 or later)
- `Node.js` (version 18 or later)
- Existing RVBuilder project(s) 

### Installation and Setup
1. Download the RVBuilder MCP package `rvbuilder-mcp.zip` from the
[**RVBuilder MCP**](https://github.com/andestech/RVBuilder/releases/tag/v1.0.0-rvbuilder-mcp) release page and extract it to a desired directory (e.g. `D:/rvbuilder-mcp`). The package contains the following components required for Codex to serve as an RVBuilder AI assistant:
    ```
    rvbuilder-mcp/
     ├── dist/
     │      └── mcp-server.js # Standalone RVBuilder MCP server 
     ├── AGENTS.md            # System prompt for Codex 
     └── resource/
            └── mcp/          # Folder of prompt and resource skills 

    ```

2.  Install `Node.js` from the official [**Node.js Download**](https://nodejs.org/en/download) page. Ensure that the installed version is 18 or later, and verify that both `Node.js` and `npm` are successfully installed and accessible:

    ``node -v`` <br>
    ``npm -v``
    
3. Install the Codex Desktop app from the [**OpenAI Codex App**](https://openai.com/zh-Hant/codex/) page or install the Codex CLI using: <br>
   ``npm install -g @openai/codex``

4. Set up the RVBuilder system prompt for Codex. 
    - If a global `AGENTS.md` does not exist in `$HOME/.codex/`, copy `AGENTS.md` from the extracted RVBuilder MCP package to the user Codex directory. 

        ```powershell
        # Powershell
        Copy-Item D:/rvbuilder-mcp/AGENTS.md -Destination $HOME/.codex/AGENTS.md 
        ```

    - If a global `AGENTS.md` already exists in `$HOME/.codex/`, append the RVBuilder system prompt to the existing file. 

        ```powershell
        # Powershell
        Get-Content D:/rvbuilder-mcp/AGENTS.md | Add-Content $HOME/.codex/AGENTS.md 
        ```

5. Edit the user configuration file `$HOME/.codex/config.toml` and add a section as follows to configure Codex to use the standalone MCP server from the extracted RVBuilderMCP package:
    ```
    [mcp_servers.rvbuilder]
    command = "node"
    args = ["D:/rvbuilder-mcp/dist/mcp-server.js"]
    ```

    For Codex Desktop app, you can alternatively configure the MCP server in "Settings > MCP servers". Add an RVBuilder MCP server and set its path to the standalone RVBuilder MCP server. <br> 

    Restart the Codex Desktop app or CLI after the configuration. <br>

### RVBuilder Development with Codex 
1. Open Codex Desktop or CLI, specify an RVBuilder project (e.g., D:/my-project).
     - In the Codex Desktop app, select the project folder.
     - In the Codex CLI, change the working directory to the project folder. 

2. Use Codex to assist with RVBuilder project development. Codex primarily supports project configuration tasks and provides guidance for development queries.

    - In the Codex Desktop app, enter your request or question in the prompt box.
    - In the Codex CLI, run `codex` followed by your request or question. For example,<br>
        - <code>codex</code> ``List the current compiler and linker options for the project.`` 
        - <code>codex</code> ``Change the compiler from GCC to Clang.``
     

## Claude Code Desktop/CLI 
### Requirements
- Claude Code Desktop (version 1.3883.0 or later) or Claude Code CLI (version 2.1.112 or later)
- `Node.js` (version 18 or later)
- Existing RVBuilder project(s)

### Installation and Setup
1. Download the RVBuilder MCP package `rvbuilder-mcp.zip` from the [**RVBuilder MCP**](https://github.com/andestech/RVBuilder/releases/tag/v1.0.0-rvbuilder-mcp) release page and extract it to a desired directory (e.g., `D:/rvbuilder-mcp`). The package contains the following components required for Claude Code to serve as an RVBuilder AI assistant:  
    ```
    rvbuilder-mcp/
     ├── dist/
     │      └── mcp-server.js # Standalone RVBuilder MCP server 
     ├── CLAUDE.md            # System prompt for Claude Code 
     └── resource/
            └── mcp/          # Folder of prompt and resource skills 

    ```

 2. Install `Node.js` from the official [**Node.js Download**](https://nodejs.org/en/download) page. Ensure that the installed version is 18 or later, and verify that both `Node.js` and `npm` are successfully installed and accessible:

    ``node -v`` <br>
    ``npm -v``

3. Install the Claude Code globally. 

    ``npm install -g @anthropic-ai/claude-code`` <br>
    
    To use the Claude Code Desktop app, download and install it from the [**Claude Download**](https://claude.ai/downloads) page.

4. Set up the RVBuilder system prompt for Claude Code.<br>
    - If a global `CLAUDE.md` does not exist, copy `CLAUDE.md` from the extracted RVBuilder MCP package to the user Claude directory. <br>
       ```powershell
       # Powershell
       Copy-Item D:/rvbuilder-mcp/CLAUDE.md -Destination $HOME/.claude/CLAUDE.md 
       ```
    - If a global `CLAUDE.md` exists in `$HOME/.claude/`, append the RVBuilder system prompt to the existing file. <br>
       ```powershell
       # Powershell
       Get-Content D:/rvbuilder-mcp/CLAUDE.md | Add-Content $HOME/.claude/CLAUDE.md 
       ```

### RVBuilder Development with Claude Code 

1. Open Claude Code Desktop or CLI, specify an RVBuilder project (e.g., D:/my-project).
    - In the Claude Code Desktop app, select the project folder.
    - In the Claude Code CLI, change the working directory to the project folder. 

2. Register the standalone MCP server in the extracted RVBuilder MCP package for the project.<br>
    ```powershell
    # Powershell
    claude mcp add -s local rvbuilder node "D:/rvbuilder-mcp/dist/mcp-server.js"
    ```
4. Use Claude Code to assist with RVBuilder project development. Claude Code primarily supports project configuration tasks and provides guidance for development queries.

    - In the Claude Code Desktop app, enter your request or question in the prompt box.
    - In the Claude Code CLI, run `claude` followed by your request or question. For example,<br>
        - <code>claude</code> ``Change the project target to ADP-AE350-A45 and update build settings`` <br>
        - <code>claude</code> ``Enable DSP for my project``<br>
        - <code>claude</code> ``What are the issues that might cause build failures?``

