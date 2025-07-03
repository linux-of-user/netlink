# NetLink v3.0

🚀 **Government-Level Secure Communication Platform**

[![Python 3.8+](https://img.shields.io/badge/python-3.8+-blue.svg)](https://www.python.org/downloads/)
[![FastAPI](https://img.shields.io/badge/FastAPI-0.115+-green.svg)](https://fastapi.tiangolo.com/)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

NetLink is a comprehensive, government-level secure communication platform designed for organizations requiring the highest levels of security, reliability, and performance. Built with modern technologies and security best practices, NetLink provides enterprise-grade communication capabilities with advanced features like distributed backup systems, AI-powered moderation, and multi-node clustering.

## ✨ Key Features

### 🔐 Government-Level Security
- **End-to-End Encryption**: AES-256 encryption for all data
- **Time-Based Crypto**: Prevents replay attacks even over HTTP
- **Multi-Factor Authentication**: Advanced permission system (Guest → Super Admin)
- **Decentralized Security**: Distributed consensus and validation
- **Rate Limiting**: Intelligent DDoS protection and abuse prevention

### 💾 Advanced Backup System
- **Distributed Shards**: Intelligent distribution across multiple nodes
- **Real-time Monitoring**: Continuous backup status tracking
- **Immutable Storage**: Tamper-proof backup segments with checksums
- **Partial Recovery**: Restore capabilities even with missing components
- **Government-Grade Redundancy**: Multiple backup locations with automatic failover

### 🚀 High Performance & Scalability
- **Multi-Node Clustering**: Horizontal scaling with load balancing
- **Database Flexibility**: SQLite, PostgreSQL, MySQL support
- **Async Architecture**: Non-blocking operations for maximum throughput
- **Plugin System**: Modular architecture for extensibility

### 🤖 AI-Powered Features
- **Content Moderation**: Machine learning-based content filtering
- **Threat Detection**: Advanced security monitoring and alerting
- **Smart Suggestions**: AI-powered user assistance

### 🔧 Advanced Administration
- **Web Admin Panel**: Comprehensive management interface
- **Desktop GUI**: Advanced desktop management application
- **CLI Tools**: Command-line administration utilities
- **Setup Wizard**: Guided configuration for new installations
- **Utility Dashboard**: Built-in development and administration tools

## 🚀 Quick Start

### One-Command Startup

#### Windows (PowerShell)
```powershell
git clone https://github.com/your-org/netlink.git
cd netlink
.\start.ps1
```

#### Linux/macOS (Bash)
```bash
git clone https://github.com/your-org/netlink.git
cd netlink
./start.sh
```

The startup scripts will automatically:
- ✅ Check Python installation
- ✅ Create virtual environment
- ✅ Install dependencies
- ✅ Create necessary directories
- ✅ Move databases to proper locations
- ✅ Start the application

### Access Points

After startup, access NetLink at:
- 🌐 **Main Interface**: http://localhost:8000
- 👨‍💼 **Admin Panel**: http://localhost:8000/admin
- ⚙️ **Setup Wizard**: http://localhost:8000/setup
- 📚 **Documentation**: http://localhost:8000/docs
- 🛠️ **Utilities**: http://localhost:8000/utils
- 🔐 **Secure Docs**: http://localhost:8000/docs-secure

### Default Credentials
- **Username**: `admin`
- **Password**: `admin123`

⚠️ **Security Notice**: Change default credentials immediately after first login!

## 📁 Project Structure

```
netlink/
├── 📄 README.md              # This file
├── 📄 requirements.txt       # Python dependencies
├── 🚀 start.ps1             # Windows startup script
├── 🚀 start.sh              # Linux/macOS startup script
├── 📁 src/netlink/app/       # Main application code
├── 📁 data/                  # Database files (auto-created)
├── 📁 logs/                  # Application logs (auto-created)
├── 📁 config/                # Configuration files (auto-created)
├── 📁 backups/               # Backup storage (auto-created)
└── 📁 plugins/               # Plugin directory (auto-created)
```

## 🔧 Configuration

### Database Options

NetLink automatically uses SQLite by default, but supports multiple databases:

#### SQLite (Default - No Setup Required)
```yaml
database:
  type: sqlite
  file_path: data/netlink.db
```

#### PostgreSQL (Production Recommended)
```yaml
database:
  type: postgresql
  host: localhost
  port: 5432
  database: netlink
  username: postgres
  password: your_password
```

#### Remote Database Hosting
NetLink supports hosted databases like:
- 🌐 **AWS RDS** (PostgreSQL/MySQL)
- 🌐 **Google Cloud SQL**
- 🌐 **Azure Database**
- 🌐 **DigitalOcean Managed Databases**
- 🌐 **Heroku Postgres**

Simply update the database configuration in the setup wizard or config files.

### Environment Variables
```bash
# Database (optional - overrides config)
DATABASE_URL=postgresql://user:pass@host:port/database

# Security
SECRET_KEY=your-secret-key
HTTPS_ENABLED=true

# Features
REDIS_URL=redis://localhost:6379
DEBUG=false
```

## 🔐 Security Features

### Multi-Level Permissions
- **Guest** (0): No access to protected resources
- **User** (1): Basic user access to own data
- **Moderator** (2): Can view user data and run basic tests
- **Admin** (3): Can manage users and run system tests
- **Super Admin** (4): Full system access including user management

### Advanced Authentication
- **Time-Based Encryption**: Prevents replay attacks
- **Session Management**: Secure token-based authentication
- **Rate Limiting**: Configurable request limits
- **IP Filtering**: Whitelist/blacklist support

### Test Users (Available by Default)
- `admin` / `admin123` (Super Admin)
- `moderator` / `mod123` (Moderator)
- `user` / `user123` (User)

## 📡 API Documentation

### Quick API Examples

#### Authentication
```bash
# Login
curl -X POST http://localhost:8000/api/v1/auth/login \
  -H "Content-Type: application/json" \
  -d '{"username": "admin", "password": "admin123"}'

# Secure Login (Time-Based Encryption)
curl -X POST http://localhost:8000/api/v1/auth/secure-login \
  -H "Content-Type: application/json" \
  -d '{"encrypted": "...", "timestamp": 1234567890, "signature": "..."}'
```

#### Messages
```bash
# Get messages (requires authentication)
curl -H "Authorization: Bearer YOUR_TOKEN" \
  http://localhost:8000/api/v1/messages

# Create message
curl -X POST http://localhost:8000/api/v1/messages \
  -H "Authorization: Bearer YOUR_TOKEN" \
  -H "Content-Type: application/json" \
  -d '{"content": "Hello World!", "author": "admin"}'
```

#### System Information
```bash
# Get system info
curl http://localhost:8000/api/v1/system/info

# Health check
curl http://localhost:8000/health
```

### Interactive API Documentation
Visit http://localhost:8000/docs for complete interactive API documentation with try-it-now functionality.

## 🛠️ Utility Tools

NetLink includes a comprehensive utility dashboard at http://localhost:8000/utils with:

- 🔐 **Password Generator**: Secure password generation
- 🆔 **UUID Generator**: Unique identifier generation
- 🔒 **Hash Generator**: MD5, SHA1, SHA256, SHA512 hashing
- 📝 **Base64 Encoder/Decoder**: Text encoding utilities
- ⏰ **Timestamp Converter**: Various timestamp formats
- 📧 **Email Validator**: Email format validation
- 🎨 **Color Palette Generator**: Random color palettes
- 📱 **QR Code Generator**: QR code creation
- 📄 **Lorem Ipsum Generator**: Placeholder text generation
- 🌐 **Network Information**: System and network details
- 📊 **System Monitor**: Real-time system information

## 🔌 Plugin System

Create custom plugins to extend NetLink functionality:

```python
from netlink.app.plugins.plugin_manager import PluginInterface, PluginMetadata

class MyPlugin(PluginInterface):
    def __init__(self):
        super().__init__()
        self.metadata = PluginMetadata(
            name="My Plugin",
            version="1.0.0",
            description="Custom functionality",
            author="Your Name"
        )
    
    def initialize(self) -> bool:
        return True
    
    def get_api_endpoints(self):
        return [{
            "path": "/api/v1/plugins/my-plugin/hello",
            "method": "GET",
            "handler": self.hello_endpoint
        }]
```

Manage plugins at: http://localhost:8000/plugins

## 🚀 Deployment

### Production Deployment
```bash
# Using Gunicorn (Recommended)
gunicorn src.netlink.app.main:app -w 4 -k uvicorn.workers.UvicornWorker

# Using Docker
docker build -t netlink .
docker run -p 8000:8000 netlink

# Direct Python
python -m uvicorn src.netlink.app.main:app --host 0.0.0.0 --port 8000
```

### Cloud Deployment
NetLink is ready for deployment on:
- 🌐 **AWS** (EC2, ECS, Lambda)
- 🌐 **Google Cloud** (Compute Engine, Cloud Run)
- 🌐 **Azure** (App Service, Container Instances)
- 🌐 **DigitalOcean** (Droplets, App Platform)
- 🌐 **Heroku** (Web Dynos)

## 🔧 Troubleshooting

### Common Issues

#### Port Already in Use
```bash
# Windows
netstat -ano | findstr :8000
taskkill /PID <PID> /F

# Linux/macOS
lsof -ti:8000 | xargs kill -9
```

#### Database Issues
```bash
# Reset database (will lose data)
rm data/netlink.db data/rate_limits.db
./start.sh  # or .\start.ps1
```

#### Permission Issues
```bash
# Linux/macOS
chmod +x start.sh
chmod -R 755 data/ logs/ config/

# Windows (Run as Administrator)
icacls data /grant Everyone:F /T
```

### Getting Help
- 📚 **Setup Wizard**: http://localhost:8000/setup
- 📖 **Documentation**: http://localhost:8000/docs
- 🛠️ **Utilities**: http://localhost:8000/utils
- 📊 **System Info**: http://localhost:8000/api/v1/system/info

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch: `git checkout -b feature/amazing-feature`
3. Make your changes
4. Add tests for new functionality
5. Ensure all tests pass: `python -m pytest`
6. Submit a pull request

### Development Setup
```bash
# Install development dependencies
pip install -r requirements.txt
pip install pytest black flake8 mypy

# Run tests
python -m pytest

# Format code
black src/

# Lint code
flake8 src/
```

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🔒 Security

For security issues, please email security@netlink.example.com instead of using the issue tracker.

## 📈 Changelog

### v3.0.0 (Latest)
- ✨ Complete rewrite with modern architecture
- 🔐 Government-level security features
- 💾 Advanced distributed backup system
- 🔌 Modular plugin system
- 🖥️ Comprehensive admin interfaces
- ⚡ Time-based encryption
- 🤖 AI-powered moderation capabilities
- ⚙️ Interactive setup wizard
- 🛠️ Built-in utility tools
- 📱 Responsive web interface

---

**NetLink v3.0** - Government-Level Secure Communication Platform  
Built with ❤️ for organizations requiring the highest levels of security and reliability.

🌟 **Star this repository if you find it useful!**
