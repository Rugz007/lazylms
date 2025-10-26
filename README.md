# 🔮 lazylms-macos

**Secure Mac-native TUI for LM Studio with Mac OS 26 Liquid Glass UI**

[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)
[![Go Version](https://img.shields.io/badge/go-1.21+-00ADD8?logo=go)](go.mod)
[![macOS](https://img.shields.io/badge/platform-macOS-000000?logo=apple)](https://www.apple.com/macos/)

A modern, secure terminal user interface for [LM Studio](https://lmstudio.ai/) featuring the revolutionary **Mac OS 26 Liquid Glass** design language. Built with [Bubble Tea](https://github.com/charmbracelet/bubbletea) for a fluid, responsive experience.

---

## ✨ Features

### 🎨 Mac OS 26 Liquid Glass UI
- **Translucent depth effects** with semi-transparent backgrounds
- **Vibrant accent colors** (cyan #00D4FF, magenta #FF006E)
- **Smooth animations** powered by Bubble Tea
- **Intuitive navigation** with vim-style keybindings

### 🔒 Security Hardening
- **Localhost-only connections** to prevent SSRF attacks
- **Input validation** for host, port, model names, and prompts
- **Path traversal protection** in model name handling
- **Timeout enforcement** on all API calls
- **Size limits** on prompts (100KB max) and model names (256 chars)

### 🚀 Performance
- **Lightweight binary** (~5MB)
- **Fast startup** (<100ms)
- **Low memory footprint** (<50MB)
- **Concurrent request handling**

### 🛠️ Developer Experience
- **Clean architecture** with internal packages
- **Comprehensive Makefile** for building, testing, and packaging
- **Mac .app bundle support** via `make app`
- **Hot reload** with `make dev`

---

## 📦 Installation

### Quick Install (Recommended)

```bash
# Clone the repository
git clone https://github.com/beauNate/lazylms-macos.git
cd lazylms-macos

# Run the installation script
chmod +x scripts/install.sh
./scripts/install.sh
```

### Manual Installation

#### Prerequisites
- Go 1.21 or later
- LM Studio (running locally)
- macOS 13.0+ (Ventura or later)

#### Build from Source

```bash
# Clone the repository
git clone https://github.com/beauNate/lazylms-macos.git
cd lazylms-macos

# Build the binary
make build

# Install to /usr/local/bin
make install
```

#### Create Mac .app Bundle

```bash
make app
# Output: build/lazylms-macos.app
```

---

## 🚀 Quick Start

See [QUICK-START.md](QUICK-START.md) for a step-by-step guide.

### Basic Usage

1. **Start LM Studio** and load a model
2. **Run lazylms-macos**:
   ```bash
   lazylms-macos
   ```
3. **Navigate** using arrow keys or vim bindings (j/k)
4. **Select a model** by pressing Enter
5. **Quit** anytime with `q` or Ctrl+C

### Command-Line Options

```bash
lazylms-macos [OPTIONS]

Options:
  --host string      LM Studio host (default: localhost)
  --port int         LM Studio port (default: 1234)
  --version          Show version information
  -h, -help          Show help
```

### Examples

```bash
# Connect to default localhost:1234
lazylms-macos

# Connect to custom port
lazylms-macos --port 8080

# Show version
lazylms-macos --version
```

---

## 🎨 Liquid Glass UI

The Mac OS 26 Liquid Glass design features:

- **Glass Background**: Semi-transparent dark (#0A0A0AE6)
- **Accent Colors**: 
  - Primary: Bright Cyan (#00D4FF)
  - Secondary: Vibrant Magenta (#FF006E)
  - Glow: Electric Teal (#00FFD4)
- **Typography**: Bold titles, soft text (#E8E8E8), dimmed hints (#666666)
- **Borders**: Rounded with glowing accents

---

## 🏗️ Architecture

```
lazylms-macos/
├── cmd/
│   └── lazylms/
│       └── main.go          # Application entry point
├── internal/
│   ├── api/
│   │   └── client.go        # LM Studio API client
│   ├── config/
│   │   └── config.go        # Configuration management
│   ├── security/
│   │   └── validation.go    # Security validation functions
│   └── ui/
│       └── model.go         # Bubble Tea UI model (Liquid Glass)
├── scripts/
│   └── install.sh           # Installation script
├── Makefile                 # Build automation
├── Info.plist              # macOS .app bundle metadata
├── go.mod                   # Go module definition
└── README.md               # This file
```

---

## 🔒 Security

### Threat Model

lazylms-macos is designed to securely interact with a **locally-running** LM Studio instance. Security features include:

1. **Localhost-only connections**: Prevents SSRF attacks by restricting connections to loopback addresses
2. **Input validation**: All user inputs are validated and sanitized
3. **Path traversal protection**: Model names are checked for path traversal attempts
4. **Resource limits**: Prompts limited to 100KB, model names to 256 characters
5. **Timeout enforcement**: All HTTP requests have strict timeouts

### Reporting Security Issues

Please report security vulnerabilities to: [security contact]

---

## 🛠️ Development

### Build Commands

```bash
make build      # Build binary to bin/lazylms-macos
make install    # Install to /usr/local/bin
make clean      # Remove build artifacts
make test       # Run tests with coverage
make run        # Build and run
make dev        # Run with hot reload (go run)
make app        # Create macOS .app bundle
make fmt        # Format code
make vet        # Run go vet
make lint       # Run golangci-lint
make deps       # Update and verify dependencies
```

### Dependencies

Manage dependencies with:

```bash
go mod tidy     # Clean up dependencies
go mod verify   # Verify checksums
```

---

## 🧪 Testing

Run tests:

```bash
make test
```

Run with coverage:

```bash
go test -v -race -coverprofile=coverage.out ./...
go tool cover -html=coverage.out
```

---

## 🤝 Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Style

- Follow standard Go formatting (`make fmt`)
- Pass all linters (`make lint`)
- Add tests for new features
- Update documentation

---

## 📄 License

MIT License - see [LICENSE](LICENSE) for details

Copyright © 2025 beauNate

---

## 🙏 Acknowledgments

- [LM Studio](https://lmstudio.ai/) - Local LLM runtime
- [Bubble Tea](https://github.com/charmbracelet/bubbletea) - Terminal UI framework
- [Lip Gloss](https://github.com/charmbracelet/lipgloss) - Style definitions
- Original [lazylms](https://github.com/Rugz007/lazylms) by Rugz007

---

## 📞 Support

- **Issues**: [GitHub Issues](https://github.com/beauNate/lazylms-macos/issues)
- **Discussions**: [GitHub Discussions](https://github.com/beauNate/lazylms-macos/discussions)
- **LM Studio Docs**: [https://lmstudio.ai/docs](https://lmstudio.ai/docs)

---

**Made with ❤️ and ☕ by beauNate**
