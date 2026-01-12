# Silvercrest

Silvercrest is strongly-typed Domain-Specific Language (DSL) for interacting with Solana blockchain data and is written in F#. This library provides a safe, functional, and composable way to query and analyze Solana chain data using F#'s powerful type system and computation expressions.

## Features

- 🔒 **Type-safe**: Leverage F#'s type system to prevent runtime errors when working with Solana data
- 🚀 **High Performance**: Efficient batching and caching strategies for optimal data retrieval
- 🧩 **Composable**: Built using F# computation expressions for elegant and maintainable queries
- 🔄 **web3.js Integration**: Seamless interop with Solana's official web3.js library
- 💪 **Strong Abstractions**: Domain-specific operations that compose well and are easy to reason about

## System Requirements

### Development Environment

#### Required Software
- **.NET SDK 9.0 or later**: Silvercrest targets .NET 9.0
  - Download from [dotnet.microsoft.com](https://dotnet.microsoft.com/download)
  - Verify installation: `dotnet --version`
- **F# Compiler**: Included with .NET SDK
  - F# 9.0 or later recommended for latest language features
- **Node.js 18.x or later**: Required for Fable compilation and web3.js interop
  - Download from [nodejs.org](https://nodejs.org/)
  - Verify installation: `node --version`
  - npm or yarn package manager

#### Recommended Development Tools
- **IDE/Editor**:
  - Visual Studio 2022 (v17.8+) with F# tools
  - Visual Studio Code with Ionide-fsharp extension
  - JetBrains Rider 2023.3 or later
- **Build Tools**:
  - FAKE (F# Make) for build automation
  - Paket or NuGet for package management
- **Version Control**: Git 2.30 or later

### Runtime Environment

#### Minimum Requirements
- **.NET Runtime**: .NET 9.0 or later
- **Memory**: 
  - Minimum: 512 MB RAM
  - Recommended: 2 GB RAM or more for heavy blockchain data queries
- **Storage**: 
  - Minimum: 50 MB for library and dependencies
  - Recommended: 500 MB+ for caching blockchain data

#### External Dependencies
- **Solana RPC Endpoint**: Access to a Solana RPC node
  - Public endpoints: Solana mainnet-beta, devnet, or testnet
  - Private RPC providers: QuickNode, Alchemy, Helius, etc.
  - Local validator for development
- **JavaScript Runtime**: Node.js or browser environment for web3.js execution
- **Network**: 
  - Stable internet connection for RPC communication
  - Recommended: Low-latency connection (<100ms to RPC endpoint)
  - Bandwidth: Varies based on query volume (1-10 Mbps recommended)

### Platform Support

#### Operating Systems
- **Windows**: Windows 10 (1607+) / Windows 11 / Windows Server 2016+
- **Linux**: 
  - Ubuntu 20.04, 22.04, 24.04 LTS
  - Debian 11, 12
  - Fedora 37+
  - Alpine Linux 3.17+
  - Other distributions with glibc 2.31+ or musl support
- **macOS**: macOS 11 (Big Sur) or later (x64 and ARM64/Apple Silicon)

#### Architecture Support
- x64 (x86_64)
- ARM64 (aarch64) - including Apple Silicon
- ARM32 (limited support, not recommended for production)

### Performance Considerations

#### Query Performance
- **Batch Size**: Configurable batch sizes for optimal RPC utilization
- **Caching**: In-memory caching for frequently accessed data
- **Concurrent Requests**: Support for parallel blockchain queries
- **Rate Limiting**: Respect RPC provider rate limits (varies by provider)

#### Recommended Hardware for Production
- **CPU**: 2+ cores (4+ cores for high-throughput applications)
- **Memory**: 4-8 GB RAM
- **Storage**: SSD recommended for better caching performance
- **Network**: 100 Mbps+ connection with low latency to Solana RPC

### Security Requirements

- **TLS/SSL**: HTTPS required for RPC endpoint communication
- **API Keys**: Secure storage for RPC provider API keys (use environment variables or secret managers)
- **Private Keys**: If handling wallet operations, use secure key management practices
  - Never log or expose private keys in error messages
  - Use hardware wallets or secure enclaves when possible
- **Dependencies**: Regularly update dependencies for security patches
  - Monitor for vulnerabilities in Fable.Core, Fable.Promise, and web3.js
  - Use `dotnet list package --vulnerable` to check for known vulnerabilities
- **Async Safety**: Properly handle F# async workflows and JavaScript promises
  - Use `async/await` patterns consistently to avoid race conditions
  - Ensure sensitive data (keys, balances) is not logged in promise rejection handlers
  - Clear sensitive data from memory when no longer needed
  - Validate all data received from Solana RPC endpoints before processing

### Browser Support (for Fable-compiled applications)

If compiling to JavaScript with Fable for browser execution:
- **Modern Browsers**:
  - Chrome/Edge 90+
  - Firefox 88+
  - Safari 14+
  - Opera 76+
- **JavaScript**: ES2015 (ES6) or later support required
- **WebAssembly**: Optional, for enhanced performance in supported browsers

### Development Dependencies

The following packages are automatically managed via NuGet:
- `Fable.Core` (4.3.0+): F# to JavaScript compiler
- `Fable.Promise` (3.2.0+): Promise handling in F#
- Additional Solana/web3.js interop packages (as specified in project file)

### Network Requirements

#### RPC Endpoint Requirements
- **Mainnet-beta**: Production Solana network
  - Public: `https://api.mainnet-beta.solana.com` (rate-limited)
  - Recommended: Private RPC provider for production use
- **Devnet**: Development network for testing
  - Public: `https://api.devnet.solana.com`
- **Testnet**: Testing network
  - Public: `https://api.testnet.solana.com`
- **Localnet**: Local validator for development
  - `http://localhost:8899` (default)

#### Firewall/Proxy Configuration
- Outbound HTTPS (443) access to Solana RPC endpoints
- WebSocket support (if using subscription features)
- Proxy configuration support via environment variables

### Compatibility Matrix

| Component | Minimum Version | Recommended Version |
|-----------|----------------|---------------------|
| .NET SDK | 9.0.0 | Latest 9.0.x |
| F# | 9.0 | Latest |
| Node.js | 18.0.0 | 20.x LTS or 22.x |
| Fable | 4.3.0 | Latest 4.x |
| Solana web3.js | 1.87.0 | Latest 1.x |

### Environment Variables

Recommended environment variables for configuration:
- `SOLANA_RPC_URL`: Solana RPC endpoint URL
- `SOLANA_NETWORK`: Network identifier (mainnet-beta, devnet, testnet)
- `RPC_API_KEY`: API key for RPC provider (if applicable)
- `SILVERCREST_CACHE_SIZE`: Maximum cache size in MB (default: 100)
- `SILVERCREST_TIMEOUT`: RPC request timeout in seconds (default: 30)

## Installation

```bash
dotnet add package Silvercrest  # Coming soon
```
