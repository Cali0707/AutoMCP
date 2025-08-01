# AutoMCP: Zero-Code MCP Server Generation

> Transform any API into an MCP server in seconds, not hours

[![Go Version](https://img.shields.io/badge/Go-1.21+-00ADD8?style=flat&logo=go)](https://golang.org/)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](LICENSE)
[![MCP Compatible](https://img.shields.io/badge/MCP-Compatible-green.svg)](https://modelcontextprotocol.io/)

**⚠️ Early Preview**: This is a research project in active development. APIs and features may change.

AutoMCP eliminates the complexity of building Model Context Protocol (MCP) servers. Instead of writing boilerplate code and learning protocol internals, simply describe your tools in a configuration file—AutoMCP handles the rest.

**Perfect for:**
- 🔌 **API Developers** - Expose existing REST APIs to AI assistants instantly
- 🤖 **AI Engineers** - Connect LLMs to external tools without custom server code  
- 🛠️ **DevOps Teams** - Integrate legacy systems with modern AI workflows

![AutoMCP System Diagram](./docs/automcp-system-diagram.jpg)

## ✨ Key Features

- **🚀 Zero-Code Server Generation** - Create MCP servers from simple YAML configs
- **📡 OpenAPI Auto-Conversion** - Transform existing OpenAPI specs into MCP servers instantly
- **🔄 Real-Time Tool Exposure** - HTTP endpoints become callable AI tools automatically
- **🛡️ Built-in Validation** - Schema validation and type safety out of the box
- **⚡ Background Processing** - Detached server mode with process management
- **🔧 Flexible Configuration** - Fine-tune which endpoints to expose and how they behave

## 🚀 Quick Start

### 1. Build the Binaries

```bash
# Clone and build
git clone https://github.com/Cali0707/AutoMCP.git
cd AutoMCP

# Build CLI and server
go build -o automcp ./cmd/automcp
go build -o automcp-server ./cmd/automcp-server

# Add to PATH (recommended)
sudo mv automcp automcp-server /usr/local/bin
```

### 2. Choose Your Own Adventure

**Option A: Convert Existing API**
```bash
automcp convert https://api.example.com/openapi.json
automcp run
```

**Option B: Create Custom Tools**
```bash
# Create mcpfile.yaml with your tools (see documentation)
automcp run
```

### 3. See It In Action
- [📹 HTTP Conversion Demo](https://youtu.be/boMyFzpgJoA) 
- [📹 Ollama Integration Demo](https://youtu.be/yqJV9rNwfg8)

## 📖 Documentation

- **[MCP File Format Guide](./docs/mcp_file_format.md)** - Learn to write custom tool configurations
- **[Examples Directory](./examples/)** - Real-world integration examples

## 💻 Usage

### Core Commands

| Command | Description | Example |
|---------|-------------|---------|
| `run` | Start MCP server | `automcp run -f myapi.yaml` |
| `stop` | Stop running server | `automcp stop` |
| `convert` | OpenAPI → MCP conversion | `automcp convert api-spec.json` |

### Starting Your Server

```bash
# Run in foreground (development)
automcp run -f /path/to/mcpfile.yaml

# Run in background
automcp run -d

# Auto-detect mcpfile.yaml in current directory
automcp run
```

### Converting Existing APIs

```bash
# From local OpenAPI file
automcp convert ./api-spec.json

# From remote OpenAPI URL
automcp convert https://api.example.com/openapi.json -o custom-name.yaml

# Petstore example
automcp convert https://petstore.swagger.io/v2/swagger.json
```

### Managing Running Servers

```bash
# Stop server (uses mcpfile.yaml to find process)
automcp stop

# Stop specific server
automcp stop -f /path/to/mcpfile.yaml
```

## 📚 Examples & Tutorials

### 🤖 Ollama Integration
**[📹 Watch Demo](https://youtu.be/yqJV9rNwfg8)** | **[View Code](./examples/ollama/)**

Connect local language models to MCP Clients with AutoMCP in two ways: by wrapping the Ollama CLI, and by wrapping the Ollama http endpoints.

**Features:**
- ✅ HTTP REST API integration
- ✅ CLI command execution  
- ✅ Model management tools

### 🔗 HTTP API Conversion
**[📹 Watch Demo](https://youtu.be/boMyFzpgJoA)** | **[View Code](./examples/http-conversion/)**

Transform any REST API into MCP tools automatically:

```bash
# 1. Convert OpenAPI spec
automcp convert http://localhost:9090/openapi.json

# 2. Run the generated MCP server
automcp run
```

**Demonstrates:**
- 🔄 Automatic OpenAPI → MCP conversion
- 🛠️ Path parameter substitution (`/features/{id}`)
- 📊 Schema validation and type safety
- 🎯 Selective endpoint exposure

---

## 🤝 Contributing

We welcome contributions! This is an early-stage research project with lots of room for improvement.

### Development Setup
```bash
git clone https://github.com/your-org/AutoMCP.git
cd AutoMCP
go mod download
go test ./...
```

## 📄 License

Apache 2.0 License - see [LICENSE](LICENSE) file for details.

## 🔗 Links

- **[Model Context Protocol](https://modelcontextprotocol.io/)** - Official MCP documentation
- **[MCP File Format](./docs/mcp_file_format.md)** - AutoMCP configuration reference
- **[Examples](./examples/)** - Real-world integration examples

---

<div align="center">
  <strong>Made with ❤️ for the AI development community</strong>
</div>
