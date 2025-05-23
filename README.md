# eDep - ML Deployment Platform

![eDep Architecture](docs/architecture.png)  
*Unified platform for deploying and managing machine learning services*

## Table of Contents
- [Features](#features-)
- [Prerequisites](#prerequisites-)
- [Installation](#installation-)
  - [Windows](#windows)
  - [Linux](#linux)
  - [macOS](#macos)
- [Usage](#usage-)
  - [Service Management](#service-management)
  - [API Endpoints](#api-endpoints)
- [Project Structure](#project-structure-)
- [Troubleshooting](#troubleshooting-)
- [Development](#development-)
- [Contributing](#contributing-)
- [License](#license-)
- [Support](#support-)

## Features ✨
- **Cross-Platform** - Windows/Linux/macOS support
- **Docker Integration** - Automated container management
- **FastAPI Backend** - RESTful API for service control
- **Real-Time Monitoring** - Service health dashboard
- **Secure Authentication** - JWT-based user system
- **Log Management** - Centralized deployment logging

## Prerequisites 📋
| Component       | Requirement              |
|-----------------|--------------------------|
| OS              | Windows 10+/Ubuntu 20.04+/macOS 12+ |
| Node.js         | v18.x LTS                |
| Python          | 3.11+                    |
| Docker          | 24.0.2+                  |
| RAM             | 8GB minimum              |
| Disk Space      | 2GB+ available           |

## Installation 🛠️

### Windows
```powershell
# 1. Clone repository
git clone https://github.com/yourusername/edep.git
cd edep/gui

# 2. Install dependencies
npm install

# 3. Build installer
npm run dist:win

# 4. Run installer
./installer/windows/edep Setup 1.0.0.exe 
```

### Linux (Debian/Ubuntu)

# 1. Install system dependencies
sudo apt update && sudo apt install -y \
    build-essential \
    docker.io \
    libgtk-3-0

# 2. Build package
cd edep/gui
npm install
npm run dist:linux

# 3. Install DEB package
sudo dpkg -i installer/linux/edep_1.0.0_amd64.deb


## Project Structure 📂
```
edep/
├── app/                   # Backend Services
│   ├── main.py            # FastAPI entrypoint
│   ├── utils/             # Deployment utilities
│   └── python/            # Embedded Python runtime
├── gui/                   # Electron Frontend
│   ├── src/               # UI components
│   │   ├── main.js        # Main process
│   │   └── renderer.js    # UI logic
│   │   ├── index.html     # Html Design
│   │   └── styles.css     # Static assets
│   └── resources/         # Static assets
├── installer/             # Platform-specific builds
├── docs/                  # Documentation
└── docker_builds/         # Generated Dockerfiles
```

This README includes:
1. Clear installation instructions for all platforms
2. Visual hierarchy with icons and tables
3. Detailed usage examples
4. Comprehensive troubleshooting guide
5. Contribution workflow
6. Multiple support channels

You should:
1. Replace `yourusername` with your GitHub handle
2. Add actual demo GIF path
3. Update support email/Docs links
4. Customize license if needed

Would you like me to add any specific sections or modify existing content?

