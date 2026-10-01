# HTTP Proxy Utility

This repository contains tools to extract HTTP requests from [mitmproxy](https://www.mitmproxy.org/) for different purposes.

## Installation

1. Install [mitmproxy](https://www.mitmproxy.org/) and [Python](https://www.python.org/downloads/).

2. Clone this repository and run the installation script.
    ```bash
    git clone https://github.com/v-yhyeo0202/proxy-utils
    cd proxy-utils
    ./install.sh
    ```

## Applications

The first function provided by this repository is to extract HTTP `PUT` and `POST` requests from [mitmproxy](https://www.mitmproxy.org/) with Python plugin and write them into bash scripts to run `az rest`. Use this function by running the command below. The requests are logged in `log` directory and will be cleaned every time the command below is run.

```bash
mitmproxy -s proxy2AzRest.py
```

The second function is to start [mitmproxy](https://www.mitmproxy.org/) with Python plugin and MCP server which listen to the HTTP traffic log sent by Python plugin. The log is intended to assist LLM to debug HTTP request related issue. Use this function by running the command below.

```bash
source venv-proxy-utils/bin/activate
python mcpServer.py
```
