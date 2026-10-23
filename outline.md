Part 1: Structured Output
Part 1A: JSON output
- create a JSON schema for classifying an image
Part 1B: image output
- use text model to write prompt for meme
- use image model to generate meme
- use image model again to edit meme
- use JSON schema from 1A to classify the meme
Part 2: MCP
- connecting idea is that model outputing JSON can control a remote server
- work through mcp for bash written in python
    ```
    from mcp.server.fastmcp import FastMCP
    mcp = FastMCP("bash")
    @mcp.tool()
    def run(command: str) -> str:
        """Run a shell command."""
        return subprocess.run(command, shell=True, capture_output=True, text=True).stdout
    mcp.run()
    ```
- use | jq to explore what it does
Part 3: sandboxing
- sandbox bash
    - cannot touch
- introduce --bind --ro-bind --dev-bind
- introduce --share-net
Part 4:
- mcp-fetch
    - combine with JSON schema to classify a webpage
- mcp-server-sqlite on the old lab
    - the default sandbox keeps us from modifying the data, even if mcp-sqlite-server is malicious
- github mcp to post an issue to the lab
    - the issue will have the image the created earlier
