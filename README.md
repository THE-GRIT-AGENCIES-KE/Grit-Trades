# G-Trades - Professional Derivative Trading Platform

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Flutter](https://img.shields.io/badge/Flutter-02569B?logo=flutter&logoColor=white)](https://flutter.dev/)
[![FastAPI](https://img.shields.io/badge/FastAPI-009688?logo=fastapi&logoColor=white)](https://fastapi.tiangolo.com/)
[![Python](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=white)](https://python.org/)

> A professional derivative trading application built with Flutter and FastAPI, connecting to Deriv's trading platform for real-time volatility index trading.

## 📋 Table of Contents

- [Overview](#overview)
- [Features](#features)
- [Architecture](#architecture)
- [Getting Started](#getting-started)
- [User Guide](#user-guide)
- [Developer Documentation](#developer-documentation)
- [API Reference](#api-reference)
- [Screenshots](#screenshots)
- [Contributing](#contributing)
- [License](#license)
- [Contact](#contact)

## 🚀 Overview

G-Trades is a professional derivative trading application that allows you to trade volatility indices and synthetic assets through the Deriv platform. It features a modern Flutter frontend with a FastAPI backend that manages WebSocket connections to Deriv's trading platform.

### What Makes G-Trades Special?

- **🎯 Specialized Focus**: Built specifically for volatility index trading
- **⚡ Real-Time Performance**: Live balance updates and instant market data
- **🔒 Security First**: Your tokens are never shared with third parties
- **📱 Cross-Platform**: Works on Android, iOS, Windows, macOS, and web browsers
- **🛡️ Secure Trading**: All trading goes directly through Deriv's official API

## ✨ Features

### Current Features (v1.0)
- ✅ **User Authentication** with Deriv API token validation
- ✅ **Real-Time Balance Updates** via WebSocket connections
- ✅ **Volatility Index Browsing** with live market data
- ✅ **Digit Contract Trading** with various durations and stakes
- ✅ **Trading History Tracking** with detailed profit/loss analysis
- ✅ **Cross-Platform Support** for all major platforms
- ✅ **Secure Token Storage** using Flutter Secure Storage
- ✅ **Dark/Light Theme Support** for user preference

### Planned Features
- 📈 Advanced charting and technical analysis
- 📊 Portfolio analytics and performance tracking
- 🔔 Price alerts and notifications
- 📱 Enhanced mobile trading features
- 🌐 Multi-language support
- 📋 Advanced order types
- 📈 Real-time market depth
- 🔄 Automated trading strategies

## 🏗️ Architecture

G-Trades follows a backend-first architecture:

```
Flutter App → FastAPI Backend → Deriv WebSocket API
     ↓              ↓                    ↓
  UI Layer    Connection Manager    Trading Data
```

### Technical Stack

#### Backend (FastAPI)
- **Framework**: FastAPI with uvicorn ASGI server
- **WebSocket Management**: Custom DerivManager class for handling multiple WebSocket connections
- **API Integration**: Direct integration with Deriv WebSocket API
- **Authentication**: Token-based authentication with automatic demo/real account detection
- **Real-time Data**: WebSocket forwarding for live balance updates and market data

#### Frontend (Flutter)
- **Framework**: Flutter with Dart
- **State Management**: Riverpod for reactive state management
- **UI Components**: Custom premium widgets with Material Design 3
- **Security**: Flutter Secure Storage for token management
- **Real-time Communication**: WebSocket client for live data updates
- **Cross-platform**: Supports Android, iOS, Web, Windows, macOS, and Linux

## 🚀 Getting Started

### Prerequisites

- Deriv account with API access
- Python 3.8+ (for backend)
- Flutter SDK (for frontend)
- Network access to Deriv servers

### Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/your-username/g-trades.git
   cd g-trades
   ```

2. **Set up the backend**
   ```bash
   cd backend
   pip install -r requirements.txt
   python main.py
   ```

3. **Set up the Flutter app**
   ```bash
   cd grit_trades_app
   flutter pub get
   flutter run
   ```

4. **Get your Deriv API token**
   - Log in to your Deriv account at [deriv.com](https://deriv.com)
   - Go to Account Settings → API Token
   - Generate a new token or copy an existing one

5. **Connect and start trading**
   - Open the G-Trades app
   - Paste your Deriv API token
   - Click "Connect to Deriv"
   - Start trading volatility indices!

## 📱 User Guide

### What Can You Do with G-Trades?

#### 1. **Connect Your Deriv Account**
- Enter your Deriv API token to securely connect your trading account
- The app automatically detects whether you're using a demo or real account
- Your account information is stored securely on your device

#### 2. **View Your Trading Dashboard**
- See your account balance in real-time
- View your profile information and account details
- Monitor your connection status to Deriv's servers
- Access quick actions to refresh your data

#### 3. **Explore Volatility Indices**
- Browse available volatility indices (like VIX-style synthetic markets)
- View market information including current prices and trading hours
- See which markets are currently open or closed
- Access detailed market information

#### 4. **Trade Digit Contracts**
- Place trades on volatility indices using digit contracts
- Choose from various contract types and durations
- Set your stake amount and trading parameters
- Execute trades directly through the app

#### 5. **Monitor Your Trading History**
- View all your past trades with detailed information
- See profit/loss for each trade
- Track your trading performance over time
- Access comprehensive trade details

### Trading Types Available

#### **Digit Contracts**
- Predict whether the last digit of a volatility index will be higher or lower
- Various contract durations (1 minute to 1 hour)
- Different stake amounts available
- Clear profit/loss calculations

#### **Volatility Indices**
- Trade on synthetic volatility markets
- 24/7 availability (unlike real markets)
- Various volatility index types
- Professional trading environment

## 👨‍💻 Developer Documentation

### Key Components

#### Backend Components
1. **DerivManager**: Central class managing WebSocket connections to Deriv
2. **FastAPI Routes**: REST endpoints for authentication and data fetching
3. **WebSocket Endpoints**: Real-time communication with Flutter clients
4. **Data Models**: Pydantic models for type-safe API responses

#### Frontend Components
1. **ProfileProvider**: Riverpod provider managing authentication state
2. **WebSocketService**: Handles real-time communication with backend
3. **API Services**: Modular services for different data types (markets, contracts, trades)
4. **Custom Widgets**: Premium UI components with consistent styling

### Data Flow
1. **Authentication**: Token validation → Account type detection → Profile retrieval
2. **Real-time Updates**: WebSocket connection → Balance streaming → UI updates
3. **Trading**: Market selection → Contract details → Purchase execution → History tracking

### Security Features
- Secure token storage using Flutter Secure Storage
- Token validation before WebSocket connection establishment
- Automatic connection cleanup and error handling
- CORS middleware for cross-origin requests

## 📚 API Reference

### REST Endpoints

| Endpoint | Method | Description |
|----------|--------|-------------|
| `/api/auth` | POST | Validate Deriv token and detect account type |
| `/api/markets` | GET | Fetch volatility indices |
| `/api/tick-history/{symbol}` | GET | Get historical price data |
| `/api/contracts/{symbol}` | GET | Get available contracts for a symbol |
| `/api/buy-contract` | POST | Execute contract purchases |
| `/api/open-contract/{contract_id}` | GET | Get open contract details |
| `/api/profit-table` | GET | Retrieve trading history |

### WebSocket Endpoints

| Endpoint | Description |
|----------|-------------|
| `WS /ws/{connection_id}` | Real-time communication channel |

### Example API Usage

```python
# Authenticate with Deriv
response = await BackendApi.validateToken(token="your_deriv_token")

# Get volatility markets
markets = await MarketsApi.fetchVolatilityMarkets(is_demo=False)

# Buy a digit contract
contract = await BuyContractApi.buyContract(
    symbol="R_10",
    contract_type="DIGIT",
    amount=10.0,
    duration=5
)
```

## 📸 Screenshots

> Screenshots will be added here showing the app interface, trading screens, and dashboard.

## 🤝 Contributing

We welcome contributions to G-Trades! Here's how you can help:

### Development Setup

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Make your changes
4. Commit your changes (`git commit -m 'Add some amazing feature'`)
5. Push to the branch (`git push origin feature/amazing-feature`)
6. Open a Pull Request

### Code Style

- Follow Flutter/Dart style guidelines
- Use meaningful commit messages
- Add tests for new features
- Update documentation as needed

### Reporting Issues

If you find a bug or have a feature request, please open an issue with:
- Clear description of the problem
- Steps to reproduce (for bugs)
- Expected vs actual behavior
- Screenshots (if applicable)

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

### MIT License

Copyright (c) 2024 The Grit Agencies

Permission is hereby granted, free of charge, to any person obtaining a copy of this software and associated documentation files (the "Software"), to deal in the Software without restriction, including without limitation the rights to use, copy, modify, merge, publish, distribute, sublicense, and/or sell copies of the Software, and to permit persons to whom the Software is furnished to do so, subject to the following conditions:

The above copyright notice and this permission notice shall be included in all copies or substantial portions of the Software.

THE SOFTWARE IS PROVIDED "AS IS", WITHOUT WARRANTY OF ANY KIND, EXPRESS OR IMPLIED, INCLUDING BUT NOT LIMITED TO THE WARRANTIES OF MERCHANTABILITY, FITNESS FOR A PARTICULAR PURPOSE AND NONINFRINGEMENT. IN NO EVENT SHALL THE AUTHORS OR COPYRIGHT HOLDERS BE LIABLE FOR ANY CLAIM, DAMAGES OR OTHER LIABILITY, WHETHER IN AN ACTION OF CONTRACT, TORT OR OTHERWISE, ARISING FROM, OUT OF OR IN CONNECTION WITH THE SOFTWARE OR THE USE OR OTHER DEALINGS IN THE SOFTWARE.

## 📞 Contact

### Developer Information

**Developed by The Grit Agencies**

- **Lead Developer**: Griffins Mbae
- **Contact**: 0743269238
- **Organization**: The Grit Agencies
- **Software**: G-Trades Professional Trading Platform
- **Version**: 1.0.0
- **Release Date**: 2024

### About The Grit Agencies

The Grit Agencies is a software development company specializing in financial technology solutions. We are committed to creating professional-grade trading applications that provide secure, reliable, and user-friendly experiences for traders worldwide.

### Support and Contact

For technical support, feature requests, or general inquiries, please contact:

- **Phone**: 0743269238
- **Developer**: Griffins Mbae
- **Organization**: The Grit Agencies

### Acknowledgments

- [Deriv.com](https://deriv.com) for providing the trading API and platform
- [Flutter team](https://flutter.dev) for the cross-platform framework
- [FastAPI team](https://fastapi.tiangolo.com) for the Python web framework
- Open source community for various libraries and tools

---

## ⚠️ Terms and Conditions

### Software License Agreement

This software is provided "as is" without warranty of any kind, either express or implied, including but not limited to the implied warranties of merchantability and fitness for a particular purpose. The entire risk as to the quality and performance of the software is with you.

### User Responsibilities

- Users are responsible for ensuring they have proper authorization to use Deriv's trading platform
- Users must comply with all applicable laws and regulations in their jurisdiction
- Users are responsible for the security of their API tokens and trading credentials
- Users acknowledge that trading involves financial risk and may result in losses

### Limitation of Liability

In no event shall the developers be liable for any direct, indirect, incidental, special, consequential, or punitive damages, including without limitation, loss of profits, data, use, goodwill, or other intangible losses, resulting from your use of the software.

### Data Privacy

- API tokens are stored securely on your device using Flutter Secure Storage
- No personal trading data is transmitted to external servers
- All trading operations are conducted directly through Deriv's official API
- Users retain full control over their trading data and credentials

### Acceptance of Terms

By using this software, you acknowledge that you have read, understood, and agree to be bound by these terms and conditions.

---

<p align="center">
  <strong>© 2024 The Grit Agencies. All rights reserved.</strong>
</p>

<p align="center">
  Made with ❤️ by <a href="tel:0743269238">Griffins Mbae</a> at <strong>The Grit Agencies</strong>
</p>
