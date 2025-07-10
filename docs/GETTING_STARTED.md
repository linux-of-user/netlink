# Getting Started with PlexiChat

Welcome to PlexiChat! This guide will get you up and running in just a few minutes.

## 🚀 Quick Start (30 seconds)

### Step 1: Get PlexiChat
```bash
git clone https://github.com/linux-of-user/plexichat.git
cd plexichat
```

### Step 2: Start Everything
```bash
python run.py
```

That's it! PlexiChat will automatically:
- ✅ Check your Python version (3.8+ required)
- ✅ Install missing dependencies
- ✅ Validate system configuration
- ✅ Start the web server
- ✅ Launch the CLI interface
- ✅ Open in split-screen mode

### Step 3: Access Your Platform

Once started, you'll see output like this:

```
============================================================
                    PLEXICHAT v1.0.0
============================================================
ℹ️  Starting in SPLIT mode...
ℹ️  Timestamp: 2024-01-01 12:00:00

✅ System validation passed
✅ Single instance lock acquired
✅ Web server started successfully
ℹ️  Access at: http://localhost:8000
ℹ️  API Docs: http://localhost:8000/docs
ℹ️  Admin: http://localhost:8000/web/admin
ℹ️  Web CLI: http://localhost:8000/web/cli

──────────────────────────────────────────────────────────
WEB SERVER RUNNING - Starting CLI Interface
──────────────────────────────────────────────────────────

✅ CLI interface ready
ℹ️  Type 'help' for available commands
ℹ️  Type 'exit' or Ctrl+C to shutdown

plexichat>
```

## 🌐 Access Points

### Web Interface
Open your browser and go to: **http://localhost:8000**

**Default Login:**
- Username: `admin`
- Password: `admin123`

### Available Interfaces
- **Main Dashboard**: http://localhost:8000
- **Admin Panel**: http://localhost:8000/web/admin
- **API Documentation**: http://localhost:8000/docs
- **Web CLI**: http://localhost:8000/web/cli

### Desktop GUI (Optional)
```bash
python plexichat_gui.py
```

## 🎮 Startup Options

### Default Mode (Recommended)
```bash
python run.py
```
- Starts web server + CLI in split-screen
- Perfect for development and administration

### Web Server Only
```bash
python run.py --web-only
```
- Production mode
- Only starts the web server
- No CLI interface

### CLI Only
```bash
python run.py --cli-only
```
- Administration mode
- Only starts the CLI
- No web server

### Force Start
```bash
python run.py --force
```
- Terminates any existing PlexiChat instance
- Useful if previous shutdown was unclean

### System Validation
```bash
python run.py --validate
```
- Checks system without starting services
- Useful for troubleshooting

## 🔧 Configuration

PlexiChat works out of the box with sensible defaults, but you can customize it:

### Environment Variables
Create a `.env` file in the PlexiChat directory:

```bash
# Server Configuration
HOST=0.0.0.0                    # Server host (default: 0.0.0.0)
PORT=8000                       # Server port (default: 8000)
WORKERS=4                       # Worker processes (default: 4)

# Database
DATABASE_URL=sqlite:///./data/plexichat.db  # Database URL

# Security
SECRET_KEY=your-secret-key-here  # JWT signing key (auto-generated)

# Logging
LOG_LEVEL=INFO                  # Logging level (DEBUG, INFO, WARNING, ERROR)
LOG_TO_FILE=true               # Enable file logging
LOG_DIR=./logs                 # Log directory

# Features
CLUSTER_ENABLED=true           # Enable clustering
DEBUG=false                    # Debug mode
```

### Quick Configuration
```bash
# Change port
echo "PORT=8080" > .env
python run.py

# Enable debug mode
echo "DEBUG=true" >> .env
python run.py
```

## 🖥️ Using the CLI

The CLI provides full control over PlexiChat:

### Basic Commands
```bash
plexichat> help              # Show all commands
plexichat> status             # System status
plexichat> info               # Detailed information
plexichat> version            # Version information
```

### System Management
```bash
plexichat> restart            # Restart server
plexichat> shutdown           # Shutdown server
plexichat> test               # Run system tests
plexichat> performance        # Performance metrics
```

### User Management
```bash
plexichat> users list         # List all users
plexichat> users create       # Create new user
plexichat> users delete       # Delete user
```

### Analytics & Monitoring
```bash
plexichat> analytics          # View analytics
plexichat> monitor status     # Monitor system
plexichat> monitor logs 50    # View recent logs
```

### Updates
```bash
plexichat> update check       # Check for updates
plexichat> update start       # Start update process
plexichat> update status      # Update status
```

### Clustering
```bash
plexichat> cluster status     # Cluster status
plexichat> cluster nodes      # List nodes
plexichat> cluster join <url> # Join cluster
```

## 🌐 Web Interface Tour

### 1. Login Page
- Clean, modern interface
- Default credentials: admin/admin123
- Remember me option
- Responsive design

### 2. Main Dashboard
- System overview
- Real-time metrics
- Quick actions
- Navigation menu

### 3. Admin Panel
- User management
- System configuration
- Update management
- Cluster monitoring
- Analytics dashboard

### 4. API Documentation
- Interactive API explorer
- Try endpoints directly
- Authentication built-in
- Complete reference

## 🔄 Hot Updates

PlexiChat supports zero-downtime updates:

### Via Web Interface
1. Go to **Admin Panel** → **Updates**
2. Click **Check for Updates**
3. If available, click **Start Hot Update**
4. Updates apply instantly without downtime!

### Via CLI
```bash
plexichat> update check
plexichat> update start
```

### What Gets Updated
- **Hot Updates**: Web interface, templates, non-core components
- **Staged Updates**: Core components (applied on restart)
- **Automatic Rollback**: Failed updates are automatically rolled back

## 🌐 Multi-Server Setup

PlexiChat automatically discovers and coordinates with other instances:

### Automatic Discovery
1. Start PlexiChat on multiple machines
2. They automatically find each other on the local network
3. Form a cluster with leader election
4. Share load and provide redundancy

### Manual Clustering
```bash
# On second machine
plexichat> cluster join http://first-machine:8000
```

### Load Balancing
```bash
# Get recommended server for new connections
curl http://localhost:8000/api/cluster/load-balance
```

## 🛑 Shutdown

### Graceful Shutdown
- **From CLI**: Type `exit` or press `Ctrl+C`
- **From Web**: Close browser (server keeps running)
- **Desktop GUI**: Click stop button

### Force Shutdown
```bash
python shutdown.py --force
```

### Clean Shutdown Script
```bash
python shutdown.py          # Interactive
python shutdown.py --list   # List processes
```

## 🧪 Testing Your Installation

### Quick Test
```bash
python quick_test.py
```

### Comprehensive Test
```bash
python final_validation.py
```

### Startup System Test
```bash
python test_startup_system.py
```

### From CLI
```bash
plexichat> test               # Run all tests
plexichat> test_health        # Quick health check
```

## 🆘 Troubleshooting

### Common Issues

#### Port Already in Use
```bash
# Check what's using the port
python shutdown.py --list

# Use different port
echo "PORT=8001" > .env
python run.py
```

#### Dependencies Missing
```bash
# Manual installation
pip install -r requirements.txt

# Or let PlexiChat handle it
python run.py  # Auto-installs dependencies
```

#### Permission Errors
```bash
# Linux/macOS: Make scripts executable
chmod +x run.sh

# Windows: Run as Administrator if needed
```

#### Can't Access Web Interface
```bash
# Check if server is running
plexichat> status

# Check firewall settings
# Make sure port 8000 is open
```

### Getting Help

#### Built-in Help
```bash
python run.py --help        # Startup options
python cli.py               # CLI help
plexichat> help               # All commands
plexichat> help <command>     # Specific command help
```

#### System Validation
```bash
python run.py --validate    # Check system
python quick_test.py        # Quick test
```

#### Documentation
- **Troubleshooting Guide**: `TROUBLESHOOTING.md`
- **API Reference**: `docs/plexichat_api.md`
- **Interactive Docs**: http://localhost:8000/docs

## 🎯 Next Steps

### For Users
1. **Explore the Web Interface** - Try all the features
2. **Create Additional Users** - Set up your team
3. **Customize Settings** - Configure to your needs
4. **Set Up Clustering** - Add more servers for redundancy

### For Developers
1. **Read the API Docs** - http://localhost:8000/docs
2. **Try the Examples** - Use the interactive API explorer
3. **Check the Code** - Explore the `app/` directory
4. **Run Tests** - `python final_validation.py`

### For Administrators
1. **Monitor System** - Use the admin dashboard
2. **Set Up Backups** - Configure data backup
3. **Plan Updates** - Use the hot update system
4. **Scale Out** - Add more servers to the cluster

## 🎉 You're Ready!

Congratulations! You now have PlexiChat running. Here's what you can do:

- ✅ **Web Interface**: Modern, responsive dashboard
- ✅ **API Access**: Complete REST API with documentation
- ✅ **CLI Control**: Full command-line administration
- ✅ **Hot Updates**: Zero-downtime updates
- ✅ **Clustering**: Multi-server coordination
- ✅ **Desktop GUI**: Native desktop application

**Happy networking with PlexiChat!** 🚀

---

Need help? Check the [Troubleshooting Guide](TROUBLESHOOTING.md) or run `python cli.py` and type `help`.
