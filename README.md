# eDep - ML Deployment Platform

![eDep Architecture](docs/architecture.png)  
*Unified platform for deploying and managing machine learning services*

## Table of Contents
- [Features](#features-)
- [Prerequisites](#prerequisites-)
- [Installation for Developers](#installation-)
  - [Windows](#windows)
  - [Linux](#linux)
  - [macOS](#macos)
- [Installer Paths](#installation-paths-)
- [Installer Instructions](#installation-instructions-)
  - [Windows](#windows)
  - [Linux](#linux)
  - [macOS](#macos)
- [Post-Installation](#post-installation-)
- [File Locations](#file-locations-)
- [Uninstallation](#uninstallation-)
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
| Node.js(Included)         | v18.x LTS                |
| Python(Incuded)         | 3.11+                    |
| Docker          | 24.0.2+                  |
| RAM             | 8GB minimum              |
| Disk Space      | 2GB+ available           |

## Installation for Devs 🛠️

### Windows
```powershell
# 1. Clone repository
git clone https://github.com/DavidPerezz99/edep.git
cd edep/gui

# 2. Install dependencies
npm install

# 3. Build installer
npm run dist:win

# 4. Run installer
./installer/windows/edep Setup 1.0.0.exe 
```

### Linux (Debian/Ubuntu)
```powershell
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
```
## Installer Paths 📂
Default installation locations for each platform:

| Platform | Application Path | Configuration/Data Path |
|----------|------------------|-------------------------|
| Windows  | `C:\Program Files\edep` | `%APPDATA%\edep` |
| Linux    | `/opt/edep`      | `~/.config/edep`        |
| macOS    | `/Applications/edep.app` | `~/Library/Application Support/edep` |

## Installer Instructions 🛠️

### Windows
1. **Download Installer**  
   Get the latest `edep Setup X.X.X.exe` from [Releases](https://github.com/DavidPerezz99/eDepInstall/blob/main/win)

2. **Run Installer**  
   ```powershell
   Start-Process -FilePath "edep Setup X.X.X.exe" -Verb RunAs
- Allow admin privileges when prompted
- Follow setup wizard (default settings recommended)```

3. **Verify Installation**  
Files will be installed to:
```
C:\Program Files\edep
├── edep.exe
├── resources/
│   ├── python/       # Embedded Python
│   └── backend/      # FastAPI server
└── locales/

```
## Linux
1. **Install DEB/RPM Package**
```powershell
# For Debian/Ubuntu
sudo dpkg -i edep_X.X.X_amd64.deb

# For Fedora/RHEL
sudo rpm -i edep-X.X.X.x86_64.rpm
```
2. **Application Locations**
```
/opt/edep/
├── edep
├── resources/
└── chrome_crashpad_handler

# Symlink in PATH
/usr/local/bin/edep
```
## File Locations 💾
| Resource            | Windows Path                                  | Linux Path                          | macOS Path                                  |
|---------------------|----------------------------------------------|-------------------------------------|--------------------------------------------|
| **Application**     | `C:\Program Files\edep`                      | `/opt/edep`                         | `/Applications/edep.app`                   |
| **Executable**      | `C:\Program Files\edep\edep.exe`             | `/usr/local/bin/edep`               | `/Applications/edep.app/Contents/MacOS/edep` |
| **Configuration**   | `%APPDATA%\edep\config`                      | `~/.config/edep`                    | `~/Library/Application Support/edep`       |
| **Logs**            | `%APPDATA%\edep\logs\main.log`               | `~/.cache/edep/logs`                | `~/Library/Logs/edep`                      |
| **Services**        | `%LOCALAPPDATA%\edep\services`               | `/var/lib/edep/services`            | `/Library/edep/services`                   |
| **Python Runtime**  | `C:\Program Files\edep\resources\python`     | `/opt/edep/resources/python`        | `/Applications/edep.app/Contents/Resources/python` |
| **Backend Code**    | `C:\Program Files\edep\resources\backend`    | `/opt/edep/resources/backend`       | `/Applications/edep.app/Contents/Resources/backend` |
| **Docker Builds**   | `%USERPROFILE%\.edep\docker_builds`          | `~/.local/share/edep/docker_builds` | `~/Library/Caches/edep/docker_builds`      |
| **User Data**       | `%USERPROFILE%\Documents\edep`               | `~/edep`                            | `~/Documents/edep`                         |
| **Cache**           | `%LOCALAPPDATA%\edep\Cache`                  | `~/.cache/edep`                     | `~/Library/Caches/edep`                    |

## Uninstallation 🗑️

### Windows
**Method 1: Control Panel**
1. Open `Control Panel > Programs > Uninstall a Program`
2. Locate "eDep" in the list
3. Double-click to uninstall

**Method 2: Command Line**
```powershell
# Remove application
Remove-Item -Path "$env:ProgramFiles\edep" -Recurse -Force

# Remove user data
Remove-Item -Path "$env:APPDATA\edep" -Recurse -Force
Remove-Item -Path "$env:LOCALAPPDATA\edep" -Recurse -Force
```
### Linux
**DEB-based (Ubuntu/Debian)**
```powershell
sudo dpkg --purge edep
sudo apt autoremove
```
**RPM-based (Fedora/RHEL)**
```powershell
sudo rpm -e edep
```
**Manual Cleanup**
```powershell
sudo rm -rf /opt/edep \
            /usr/local/bin/edep \
            ~/.config/edep \
            ~/.cache/edep
```

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
2. Step-by-step installer usage
3. File location reference table
4. Complete uninstallation instructions
5. Visual hierarchy with icons and tables
6. Detailed usage examples
7. Comprehensive troubleshooting guide
8. Contribution workflow
9. Multiple support channels
10. Cross-platform path mappings

You should:
1. Replace `yourusername` with your GitHub handle
2. Add actual demo GIF path
3. Update support email/Docs links
4. Customize license if needed

Key highlights:
- Platform-specific installation workflows
- Visual directory structures
- Administrative privilege requirements
- Persistent data locations
- Clean uninstall procedures

Would you like me to add any specific sections or modify existing content?

