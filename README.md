# Azure REST API HTTP Proxy Utility

This repository contains tools to extract Azure REST API HTTP traffics from [mitmproxy](https://www.mitmproxy.org/) for different purposes.

## Installation

1. Install [mitmproxy](https://www.mitmproxy.org/) and [Python](https://www.python.org/downloads/).

2. Clone this repository and run the installation script.
    ```bash
    git clone https://github.com/v-yhyeo0202/proxy-utils
    cd proxy-utils
    ./install.sh
    ```

3. Configure `path.main` in `config.yml` as the absolute path of this repository directory.

## Applications

The first function provided by this repository is to extract HTTP `PUT` and `PATCH` requests from [mitmproxy](https://www.mitmproxy.org/) with Python plugin and write them into bash scripts to run `az rest`. Use this function by running the command below. The requests are logged in `log` directory and will be cleaned every time the command below is run.

```bash
mitmproxy -s proxy2AzRest.py
```

The second function is to start [mitmproxy](https://www.mitmproxy.org/) with Python plugin and MCP server which listen to the HTTP traffic log (requests and responses of `PUT` and `PATCH` operations) sent by Python plugin. The log is intended to assist LLM to debug HTTP traffic issue related to Azure REST API. Follow the steps below to use the MCP server.

1. Configure `config.yml`.
    * `port.mcpServerProxy`: Port number of mitmproxy which sends HTTP traffic logs to MCP server.
    * `port.mcpServer`: Port number of MCP server.

2. Start mitmproxy and MCP server by running the following command.
    ```bash
    ./mcpServer.sh
    ```
