# Polymarket Copy Trading Bot

> Enterprise-grade automated copy trading system for Polymarket that mirrors trades from top performers with intelligent position sizing, real-time execution, and comprehensive risk management.

[![License: ISC](https://img.shields.io/badge/License-ISC-blue.svg)](LICENSE)
[![Node.js Version](https://img.shields.io/badge/node-%3E%3D18.0.0-brightgreen.svg)](https://nodejs.org/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.7-blue.svg)](https://www.typescriptlang.org/)
[![Code Quality](https://img.shields.io/badge/Code%20Quality-Professional-green.svg)](docs/CODE_QUALITY_IMPROVEMENTS.md)

## Contact 

| Platform | Link |
|----------|------|
| 📱 Telegram | [t.me/novustch](https://t.me/novustch) |
| 📲 WhatsApp | [wa.me/14105015750](https://wa.me/14105015750) |
| 💬 Discord | [discordapp.com/users/985432160498491473](https://discordapp.com/users/985432160498491473)

<div align="left">
    <a href="https://t.me/novustch" target="_blank"><img alt="Telegram"
        src="https://img.shields.io/badge/Telegram-26A5E4?style=for-the-badge&logo=telegram&logoColor=white"/></a>
    <a href="https://wa.me/14105015750" target="_blank"><img alt="WhatsApp"
        src="https://img.shields.io/badge/WhatsApp-25D366?style=for-the-badge&logo=whatsapp&logoColor=white"/></a>
    <a href="https://discordapp.com/users/985432160498491473" target="_blank"><img alt="Discord"
        src="https://img.shields.io/badge/Discord-7289DA?style=for-the-badge&logo=discord&logoColor=white"/></a>
</div>

Feel free to reach out for implementation assistance or integration support.

## Table of Contents

- [Overview](#overview)
  - [How It Works](#how-it-works)
- [Key Features](#key-features)
  - [Core Functionality](#core-functionality)
  - [Technical Features](#technical-features)
  - [Monitoring Method](#monitoring-method)
- [Architecture](#architecture)
  - [System Components](#system-components)
  - [Technology Stack](#technology-stack)
- [Quick Start](#quick-start)
  - [Prerequisites](#prerequisites)
  - [Installation](#installation)
  - [First-Time Setup](#first-time-setup)
- [Configuration](#configuration)
  - [Environment Variables](#environment-variables)
  - [Copy Strategy Configuration](#copy-strategy-configuration)
  - [Finding Traders](#finding-traders)
- [Deployment](#deployment)
  - [Docker Deployment (Recommended)](#docker-deployment-recommended)
  - [Manual Deployment](#manual-deployment)
  - [Production Considerations](#production-considerations)
- [Documentation](#documentation)
  - [Getting Started](#getting-started)
  - [Advanced Guides](#advanced-guides)
  - [Testing & Analysis](#testing--analysis)
  - [Development](#development)
- [Safety & Risk Management](#safety--risk-management)
  - [Important Disclaimers](#important-disclaimers)
  - [Risk Management Best Practices](#risk-management-best-practices)
  - [Safety Features](#safety-features)
- [Troubleshooting](#troubleshooting)
  - [Common Issues](#common-issues)
  - [Diagnostic Commands](#diagnostic-commands)
- [Contributing](#contributing)
  - [Development Guidelines](#development-guidelines)
- [Advanced Version](#advanced-version)
- [Trading Tool](#trading-tool)
- [License](#license)
- [Acknowledgments](#acknowledgments)
- [Support](#support)

<a id="#overview"></a>
## Overview

The Polymarket Copy Trading Bot is a production-ready TypeScript application that automatically replicates trades from successful Polymarket traders to your wallet. Built with enterprise-grade code quality standards, the bot provides:

- **Real-time Trade Monitoring**: Continuous monitoring of selected traders using Polymarket Data API
- **Intelligent Position Sizing**: Automatic calculation of proportional trade sizes based on capital ratios
- **Advanced Risk Management**: Built-in safeguards including slippage protection, position limits, and balance checks
- **Persistent Data Storage**: Complete trade history and position tracking via MongoDB
- **Professional Codebase**: Type-safe, well-documented, and maintainable code following industry best practices

### How It Works

<img width="995" height="691" alt="Architecture Diagram" src="https://github.com/user-attachments/assets/79715c7a-de2c-4033-81e6-b2288963ec9b" />

1. **Trader Selection** - Identify top performers from [Polymarket Leaderboard](https://polymarket.com/leaderboard) or [Predictfolio](https://predictfolio.com)
2. **Continuous Monitoring** - Bot polls trader positions at configurable intervals (default: 1 second)
3. **Position Calculation** - Automatically scales trades based on your balance vs. trader's portfolio value
4. **Order Execution** - Places matching orders on Polymarket using your wallet via CLOB API
5. **Performance Tracking** - Maintains comprehensive trade history and position data in MongoDB

<a id="#key-features"></a>
## Key Features

### Core Functionality

- **Multi-Trader Support** - Simultaneously track and copy trades from multiple traders
- **Smart Position Sizing** - Automatic trade size calculation with configurable strategies (Percentage, Fixed, Adaptive)
- **Tiered Multipliers** - Apply different multipliers based on trade size thresholds
- **Position Tracking** - Accurate tracking of purchases and sells, even after balance changes
- **Trade Aggregation** - Combines multiple small trades into larger executable orders (optional)
- **Real-time Execution** - Sub-second trade detection and execution
- **Price Protection** - Built-in slippage checks to prevent unfavorable fills

### Technical Features

- **Type-Safe Codebase** - Full TypeScript implementation with strict type checking
- **Error Handling** - Comprehensive error handling with custom error classes
- **Database Integration** - MongoDB for persistent storage of trades and positions
- **Configuration Management** - Environment-based configuration with validation
- **Logging System** - Structured logging with file output and console display
- **Health Monitoring** - Built-in health check system for configuration validation

### Monitoring Method

The bot currently uses the **Polymarket Data API** to monitor trader activity and detect new positions. The monitoring system polls trader positions at configurable intervals (default: 1 second) to ensure timely trade detection and execution.

**🚀 Roadmap:** Future versions will migrate to **RTDS (Real-Time Data Stream)** for even faster trade detection with lower latency and reduced API load, enabling near-instantaneous trade replication.

<img width="680" height="313" alt="Monitoring Architecture" src="https://github.com/user-attachments/assets/d868f9f2-a1dd-4bfe-a76e-d8cbdfbd8497" />

<a id="#architecture"></a>
## Architecture

### System Components

```
┌─────────────────┐
│  Trade Monitor  │ → Monitors trader activity via Polymarket API
└────────┬────────┘
         │
         ↓
┌─────────────────┐
│  Trade Executor │ → Executes trades based on copy strategy
└────────┬────────┘
         │
         ↓
┌─────────────────┐
│  CLOB Client    │ → Interfaces with Polymarket CLOB API
└─────────────────┘
         │
         ↓
┌─────────────────┐
│   MongoDB       │ → Stores trade history and positions
└─────────────────┘
```

### Technology Stack

- **Runtime**: Node.js 18+
- **Language**: TypeScript 5.7
- **Database**: MongoDB (Atlas supported)
- **Blockchain**: Polygon Network
- **APIs**: Polymarket CLOB Client, Polymarket Data API
- **Infrastructure**: Docker support for containerized deployment

<a id="#quick-start"></a>
## Quick Start

### Prerequisites

Before installing, ensure you have:

- **Node.js** v18.0.0 or higher ([Download](https://nodejs.org/))
- **MongoDB Database** - [MongoDB Atlas](https://www.mongodb.com/cloud/atlas/register) (free tier supported)
- **Polygon Wallet** - Wallet with USDC balance and POL/MATIC for gas fees
- **RPC Endpoint** - Polygon RPC endpoint from [Infura](https://infura.io), [Alchemy](https://www.alchemy.com), or [Ankr](https://www.ankr.com)

### Installation

```bash
# Clone the repository
git clone https://github.com/Novus-Tech-LLC/Polymarket-Copytrading-Bot.git
cd polymarket-copy-trading-bot

# Install dependencies
npm install

# Run interactive setup wizard
npm run setup

# Build the project
npm run build

# Verify configuration
npm run health-check

# Start the bot
npm start
```

### First-Time Setup

1. **Run Setup Wizard**: Execute `npm run setup` to interactively configure your `.env` file
2. **Verify Configuration**: Run `npm run health-check` to validate all settings
3. **Fund Your Wallet**: Ensure your Polygon wallet has sufficient USDC and POL/MATIC
4. **Select Traders**: Add trader addresses to `USER_ADDRESSES` in your `.env` file
5. **Start Monitoring**: Run `npm start` to begin trading

**📖 For detailed setup instructions, see [Getting Started Guide](./docs/GETTING_STARTED.md)**

<a id="#configuration"></a>
## Configuration

### Environment Variables

The bot is configured via environment variables. Essential variables include:

| Variable | Description | Example | Required |
|----------|-------------|---------|----------|
| `USER_ADDRESSES` | Comma-separated trader addresses to copy | `'0xABC...,0xDEF...'` | ✅ |
| `PROXY_WALLET` | Your Polygon wallet address | `'0x123...'` | ✅ |
| `PRIVATE_KEY` | Wallet private key (no 0x prefix) | `'abc123...'` | ✅ |
| `MONGO_URI` | MongoDB connection string | `'mongodb+srv://...'` | ✅ |
| `RPC_URL` | Polygon RPC endpoint | `'https://polygon...'` | ✅ |
| `USDC_CONTRACT_ADDRESS` | USDC token contract | `'0x2791Bca1f2de4661ED88A30C99A7a9449Aa84174'` | ✅ |
| `CLOB_HTTP_URL` | CLOB HTTP endpoint | `'https://clob.polymarket.com/'` | ✅ |
| `CLOB_WS_URL` | CLOB WebSocket endpoint | `'wss://ws-subscriptions-clob.polymarket.com/ws'` | ✅ |
| `COPY_STRATEGY` | Copy strategy (PERCENTAGE, FIXED, ADAPTIVE) | `'PERCENTAGE'` | ❌ |
| `COPY_SIZE` | Copy size parameter | `10.0` | ❌ |
| `TRADE_MULTIPLIER` | Position size multiplier | `1.0` | ❌ |
| `MAX_ORDER_SIZE_USD` | Maximum order size in USD | `100.0` | ❌ |
| `MIN_ORDER_SIZE_USD` | Minimum order size in USD | `1.0` | ❌ |
| `FETCH_INTERVAL` | Polling interval in seconds | `1` | ❌ |
| `TRADE_AGGREGATION_ENABLED` | Enable trade aggregation | `false` | ❌ |

### Copy Strategy Configuration

The bot supports three copy strategies:

1. **PERCENTAGE** - Copy a fixed percentage of trader's order size
2. **FIXED** - Copy a fixed dollar amount per trade
3. **ADAPTIVE** - Dynamically adjust percentage based on trader's order size

See [Copy Strategy Documentation](./docs/TIERED_MULTIPLIERS.md) for detailed configuration options.

### Finding Traders

To identify traders worth copying:

1. Visit [Polymarket Leaderboard](https://polymarket.com/leaderboard)
2. Look for traders with:
   - Positive P&L over extended periods
   - Win rate above 55%
   - Active trading history
   - Consistent performance
3. Verify detailed statistics on [Predictfolio](https://predictfolio.com)
4. Add wallet addresses to `USER_ADDRESSES` in your `.env` file

**📖 For complete configuration guide, see [Quick Start Guide](./docs/QUICK_START.md)**

<a id="#deployment"></a>
## Deployment

### Docker Deployment (Recommended)

Deploy with Docker Compose for a production-ready, containerized setup:

```bash
# Copy environment template
cp .env.example .env

# Edit .env with your configuration
nano .env

# Start the container
docker-compose up -d

# View logs
docker-compose logs -f polymarket

# Stop the container
docker-compose down
```

**📖 [Complete Docker Deployment Guide →](./docs/DOCKER.md)**

### Manual Deployment

For manual deployment on a server:

```bash
# Install dependencies
npm install

# Build the project
npm run build

# Start with process manager (PM2 recommended)
pm2 start dist/index.js --name polymarket-bot

# Monitor logs
pm2 logs polymarket-bot
```

### Production Considerations

- Use a process manager (PM2, systemd, etc.) for automatic restarts
- Set up log rotation for log files
- Monitor system resources and API rate limits
- Configure alerts for critical errors
- Regular database backups
- Keep dependencies updated

<a id="#documentation"></a>
## Documentation

### Getting Started

- **[🚀 Getting Started Guide](./docs/GETTING_STARTED.md)** - Complete beginner's guide with step-by-step instructions
- **[⚡ Quick Start](./docs/QUICK_START.md)** - Fast setup guide for experienced users

### Advanced Guides

- **[🐳 Docker Deployment](./docs/DOCKER.md)** - Complete container deployment guide
- **[👥 Multi-Trader Guide](./docs/MULTI_TRADER_GUIDE.md)** - Configuring and managing multiple traders
- **[📍 Position Tracking](./docs/POSITION_TRACKING.md)** - Understanding position tracking mechanics
- **[💰 Funding Guide](./docs/FUNDING_GUIDE.md)** - Wallet funding and token management
- **[📊 Tiered Multipliers](./docs/TIERED_MULTIPLIERS.md)** - Advanced position sizing strategies

### Testing & Analysis

- **[🧪 Simulation Guide](./docs/SIMULATION_GUIDE.md)** - Backtesting trading strategies
- **[🔬 Simulation Runner](./docs/SIMULATION_RUNNER_GUIDE.md)** - Advanced backtesting tools

### Development

- **[📝 Code Quality Improvements](./docs/CODE_QUALITY_IMPROVEMENTS.md)** - Technical documentation on code quality standards

<a id="#safety--risk-management"></a>
## Safety & Risk Management

### ⚠️ Important Disclaimers

**This software executes real trades with real money. Use at your own risk.**

- **No Guarantees** - Past performance does not guarantee future results
- **Financial Risk** - Trading involves risk of financial loss
- **No Liability** - Developers are not responsible for financial losses
- **Educational Purpose** - This software is provided for educational purposes

### Risk Management Best Practices

1. **Start Small** - Test with minimal funds before scaling up
2. **Diversify** - Copy multiple traders with different strategies
3. **Monitor Regularly** - Check bot logs and positions daily
4. **Set Limits** - Use position size limits and daily volume caps
5. **Dedicated Wallet** - Use a separate wallet from your main funds
6. **Emergency Stop** - Know how to stop the bot quickly (Ctrl+C or process manager)
7. **Research Traders** - Thoroughly research traders before copying
8. **Stay Informed** - Monitor market conditions and bot performance

### Safety Features

- **Balance Checks** - Automatic balance verification before trades
- **Slippage Protection** - Price validation to prevent unfavorable fills
- **Position Limits** - Configurable maximum position sizes
- **Daily Volume Caps** - Optional daily trading volume limits
- **Error Handling** - Comprehensive error handling and recovery
- **Health Checks** - Configuration validation before startup

<a id="#troubleshooting"></a>
## Troubleshooting

### Common Issues

#### Configuration Issues

**Missing environment variables**
```bash
# Run setup wizard
npm run setup

# Or manually create .env file from .env.example
cp .env.example .env
```

**Invalid configuration**
```bash
# Run health check to validate
npm run health-check
```

#### Database Issues

**MongoDB connection failed**
- Verify `MONGO_URI` is correct
- Whitelist your IP address in MongoDB Atlas
- Check network connectivity
- Verify database credentials

#### Trading Issues

**Bot not detecting trades**
- Verify trader addresses in `USER_ADDRESSES`
- Check trader has recent activity
- Verify `FETCH_INTERVAL` is appropriate
- Check MongoDB connection

**Insufficient balance errors**
- Add USDC to your wallet
- Ensure POL/MATIC for gas fees
- Check token allowances
- Run `npm run check-allowance`

**Orders failing**
- Verify wallet has sufficient balance
- Check token allowances
- Review slippage settings
- Check network connectivity

### Diagnostic Commands

```bash
# Health check
npm run health-check

# Check token allowance
npm run check-allowance

# Verify wallet balance
npm run check-both

# View recent activity
npm run check-activity

# Check positions
npm run check-stats
```

**📖 For detailed troubleshooting, see [Quick Start Guide](./docs/QUICK_START.md)**

<a id="#contributing"></a>
## Contributing

We welcome contributions! Please follow these guidelines:

1. **Fork the repository**
2. **Create a feature branch** (`git checkout -b feature/amazing-feature`)
3. **Follow code quality standards** - See [Code Quality Improvements](./docs/CODE_QUALITY_IMPROVEMENTS.md)
4. **Write tests** for new features
5. **Update documentation** as needed
6. **Commit your changes** (`git commit -m 'Add amazing feature'`)
7. **Push to the branch** (`git push origin feature/amazing-feature`)
8. **Open a Pull Request**

### Development Guidelines

- Follow TypeScript best practices
- Maintain type safety (no `any` types)
- Add JSDoc comments for public APIs
- Write meaningful commit messages
- Update relevant documentation
- Test thoroughly before submitting


<a id="#license"></a>
## License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- **[Polymarket CLOB Client](https://github.com/Polymarket/clob-client)** - Official Polymarket CLOB API client
- **[Predictfolio](https://predictfolio.com)** - Trader analytics and performance metrics
- **Polygon Network** - Layer 2 blockchain infrastructure

## Advanced Version

**🚀 Version 2 Available:** An advanced version with **RTDS (Real-Time Data Stream)** monitoring is now available as a private repository.

Version 2 features the fastest trade detection method with near-instantaneous trade replication, lower latency, and reduced API load. Copy trading works excellently in the advanced version.

<img width="680" height="313" alt="Monitoring Architecture" src="https://github.com/user-attachments/assets/d868f9f2-a1dd-4bfe-a76e-d8cbdfbd8497" />

### Key Advantages of Version 2

- **Real-Time Data Stream (RTDS)** - Instant trade detection without polling delays
- **Lower Latency** - Near-instantaneous trade replication for optimal entry prices
- **Reduced API Load** - More efficient API usage compared to polling methods
- **Enhanced Performance** - Superior copy trading execution with minimal delay
- **Scalability** - Better handling of multiple traders and high-frequency trading

For access to the advanced version, please contact us through the [Support](#support) channels.

## Trading Tool

I've also developed a trading bot for Polymarket built with **Rust**, providing high-performance trading capabilities with low-level system control.

<img width="1917" height="942" alt="Rust Trading Bot" src="https://github.com/user-attachments/assets/08a5c962-7f8b-4097-98b6-7a457daa37c9" />

**Video Demo:** [Watch on YouTube](https://youtu.be/X5l8x4Ae2QQ)

### Rust Trading Bot Features

- **High Performance** - Built with Rust for maximum speed and efficiency
- **Low Latency** - Optimized for minimal execution delay
- **System-Level Control** - Direct system access for advanced trading strategies
- **Memory Safety** - Rust's memory safety guarantees without garbage collection overhead
- **Production Ready** - Battle-tested for reliable trading operations

## Support

For questions, issues, or support:

- **Telegram**: [Novus Tech](https://t.me/novustch)
- **Issues**: [GitHub Issues](https://github.com/Novus-Tech-LLC/Polymarket-Copytrading-Bot/issues)
- **Documentation**: See [Documentation](#documentation) section above

---

**Legal Disclaimer:** This software is provided "as is" for educational purposes only. Trading cryptocurrencies and prediction markets involves substantial risk of loss. The developers, contributors, and maintainers of this software are not responsible for any financial losses, damages, or other consequences resulting from the use of this software. Users are solely responsible for their trading decisions and should consult with qualified financial advisors before engaging in any trading activities.
