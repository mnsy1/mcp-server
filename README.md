# MCP Server Implementation

This repository contains a **Model Context Protocol (MCP)** server designed to extend the capabilities of AI models.

## What is MCP?
The Model Context Protocol (MCP) is an open standard that enables seamless integration between AI models and local or remote data sources. It acts as a universal connector, allowing LLMs to safely access tools, files, and APIs through a standardized interface.

## Key Benefits
* **Universal Compatibility:** Build a tool once and use it across any AI agent or IDE that supports the MCP standard.
* **Enhanced Context:** Provides LLMs with real-time, secure access to your local files, databases, and proprietary workflows.
* **Standardized Security:** Offers a controlled environment where the AI can only interact with the specific resources you expose through the server.
* **Reduced Friction:** Eliminates the need to write custom "glue code" for every new AI tool or integration.

---

## Getting Started

### Prerequisites
* Python 3.10+
* [PyCharm](https://www.jetbrains.com/pycharm/) or Any IDE
* An MCP-compatible client
* `uv` package manager

### Installing `uv` Package Manager

Windows (PowerShell):
```shell
powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
```
On MacOS/Linux:
```shell
curl -LsSf https://astral.sh/uv/install.sh | sh
```
Pip:
```shell
pip install uv
```

### Installation
1. Clone the repository:
```shell
git clone https://github.com/mnsy1/mcp-server.git
```
2. Install Dependencies:
```shell
uv add -r requirements.txt
```
3. Start the MCP server:
```shell
uv run main.py
```
### Debug
```shell
npx @modelcontextprotocol/inspector uv run main.py
```

## Connecting MCP to `Continue` Plugin at PyCharm:
### Add `Continue` Plugin to PyCharm/VS Code:
- Search for `Continue` Plugin
### Connect MCP Tool to Continue:
1. In your project root, create a folder named .continue/mcpServers/.
2. Create a file inside named docs-tool.yaml.
3. Paste the following:
```shell
name: Docs Search MCP
version: 0.0.1
schema: v1
mcpServers:
  - name: docs-tool
    type: stdio
    command: "C:/ABSOLUTE/PATH/TO/YOUR/uv" # C:/Users/USERNAME/.local/bin/uv
    args:
      - "--directory"
      - "C:/ABSOLUTE/PATH/TO/YOUR/mcp-server-folder"
      - "run"
      - "main.py"
```
### Check Connection of MCP Tool at Continue:
Navigate to Settings ==> Tools

![Successfully Connect the MCP tool](https://github.com/mnsy1/mcp-server/blob/master/images/Screenshot%202026-03-13%20172454.png)

## Using MCP Server:
Ask your Agent any question related to the documentation Ex: how do i implement a chroma db in langchain?

![Successfully Used MCP tool](https://github.com/mnsy1/mcp-server/blob/master/images/Screenshot%202026-03-13%20151930.png)

