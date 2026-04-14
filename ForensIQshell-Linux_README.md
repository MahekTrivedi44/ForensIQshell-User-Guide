# ForensIQshell - Linux Distribution 🛡️

## Overview
ForensIQshell is an AI-powered forensic shell command assistant that helps cybersecurity professionals and ethical hackers generate accurate shell commands for Linux environments. It combines the power of Groq's LLM with a sophisticated RAG (Retrieval-Augmented Generation) system to provide context-aware command suggestions.

## Features
- 🤖 **AI-Powered Command Generation**: Uses Groq's Llama 3.1 model for intelligent command suggestions
- 📚 **RAG-Enhanced Context**: Leverages LlamaIndex with forensic documentation for better accuracy
- 🐧 **Linux-Specific**: Optimized for various Linux distributions and shell environments
- 🛡️ **Security-Focused**: Designed for ethical hacking and cybersecurity tasks
- ⚡ **Interactive Execution**: Step-by-step command confirmation and execution
- 🔒 **PyArmor Protected**: Source code is obfuscated for security

## System Requirements
- **Operating System**: Linux (Ubuntu 18.04+, CentOS 7+, Debian 9+, Fedora 30+, or equivalent)
- **Python**: 3.8 or higher
- **Memory**: Minimum 4GB RAM (8GB recommended)
- **Storage**: At least 2GB free space
- **Internet**: Required for Groq API calls and initial setup
- **Build Tools**: gcc, make, python3-dev (for some dependencies)

## Installation & Setup

### Step 1: Update System Packages
**Ubuntu/Debian:**
```bash
sudo apt update && sudo apt upgrade -y
sudo apt install python3 python3-pip python3-venv python3-dev build-essential -y
```

**CentOS/RHEL/Fedora:**
```bash
# CentOS/RHEL
sudo yum update -y
sudo yum install python3 python3-pip python3-devel gcc gcc-c++ make -y

# Fedora
sudo dnf update -y
sudo dnf install python3 python3-pip python3-devel gcc gcc-c++ make -y
```

**Arch Linux:**
```bash
sudo pacman -Syu
sudo pacman -S python python-pip base-devel
```

### Step 2: Verify Python Installation
Check your Python version:
```bash
python3 --version
pip3 --version
```

### Step 3: Extract and Navigate
1. Extract the `dist_linux` folder to your desired location
2. Open Terminal
3. Navigate to the extracted folder:
```bash
cd /path/to/dist_linux
```

### Step 4: Create Virtual Environment (Recommended)
```bash
python3 -m venv forensiq_env
source forensiq_env/bin/activate
```

### Step 5: Install Dependencies
Install all required Python packages:
```bash
pip install --upgrade pip
pip install -r requirements.txt
```

**Note**: This may take 5-10 minutes as it installs machine learning libraries including PyTorch.

### Step 6: Configure API Key
You need a Groq API key to use ForensIQshell:

1. Get your free API key from [Groq Console](https://console.groq.com/)
2. Set it as an environment variable:

**Temporary (current session):**
```bash
export GROQ_API_KEY="your_api_key_here"
```

**Permanent setup (recommended):**
Add to your shell profile (`~/.bashrc`, `~/.zshrc`, or `~/.profile`):
```bash
echo 'export GROQ_API_KEY="your_api_key_here"' >> ~/.bashrc
source ~/.bashrc
```

## Running ForensIQshell

### Method 1: With Virtual Environment
```bash
cd /path/to/dist_linux
source forensiq_env/bin/activate
python3 app.py
```

### Method 2: Direct Execution
```bash
cd /path/to/dist_linux
python3 app.py
```

### Method 3: Make Executable
```bash
chmod +x app.py
./app.py
```

### Method 4: System Service (Advanced)
Create a systemd service for background operation:
```bash
sudo nano /etc/systemd/system/forensiqshell.service
```

## Usage Guide

### Starting the Application
When you run ForensIQshell, you'll see:
```
Welcome to ForensIQshell 🛡️
Please keep checking the main site for updates.
For inquiries, feedback, or issues with the app, contact: ForensIQally@outlook.com
-----------------------------------------------------------------------------------
Detected environment: linux
Loading documents from: data/linux
RAG system initialized successfully!
Type 'exit' or 'quit' to stop, or 'contact' for support information.

🔍 Your forensic shell request:
```

### Example Commands
Try these example requests:

**Network Analysis:**
```
🔍 Your forensic shell request: scan all open ports on 192.168.1.1
🔍 Your forensic shell request: monitor network traffic on eth0
🔍 Your forensic shell request: find all active network connections
```

**System Information:**
```
🔍 Your forensic shell request: get detailed system information including kernel version
🔍 Your forensic shell request: check system resource usage
🔍 Your forensic shell request: list all installed packages
```

**Process Investigation:**
```
🔍 Your forensic shell request: find all running processes with network connections
🔍 Your forensic shell request: identify processes using high CPU
🔍 Your forensic shell request: check for suspicious processes
```

**File Analysis:**
```
🔍 Your forensic shell request: search for recently modified files in /home
🔍 Your forensic shell request: find files with SUID permissions
🔍 Your forensic shell request: analyze file permissions in /etc
```

**Linux-Specific Forensics:**
```
🔍 Your forensic shell request: check system logs for failed login attempts
🔍 Your forensic shell request: analyze systemd journal for errors
🔍 Your forensic shell request: find all cron jobs on the system
🔍 Your forensic shell request: check for rootkits using chkrootkit
```

### Command Execution Flow
1. **Request**: Enter your forensic task in natural language
2. **Generation**: AI generates appropriate Linux commands
3. **Review**: Each command is displayed with explanation
4. **Confirmation**: Choose to execute (yes/no/all/skip-remaining)
5. **Execution**: Commands run in your shell environment
6. **Results**: View output and any errors

### Special Commands
- `exit` or `quit`: Close the application
- `contact`: Display support information

## Linux-Specific Features

### Distribution Detection
ForensIQshell automatically adapts to your Linux distribution:
- **Debian/Ubuntu**: Uses `apt`, `dpkg`, `systemctl`
- **Red Hat/CentOS/Fedora**: Uses `yum`/`dnf`, `rpm`, `systemctl`
- **Arch Linux**: Uses `pacman`, `systemctl`
- **SUSE**: Uses `zypper`, `systemctl`
- **Alpine**: Uses `apk`

### Tool Installation
The AI can automatically install Linux tools using:
- **APT** (Debian/Ubuntu): `apt-get install`
- **YUM/DNF** (RHEL/CentOS/Fedora): `yum install` / `dnf install`
- **Pacman** (Arch): `pacman -S`
- **Snap**: Universal packages
- **Flatpak**: Sandboxed applications
- **Source compilation**: For specialized tools

### Security Integration
- **SELinux**: Respects Security-Enhanced Linux policies
- **AppArmor**: Works with Ubuntu/SUSE security framework
- **Sudo**: Proper privilege escalation handling
- **Firewall**: Integration with iptables, ufw, firewalld

## Troubleshooting

### Common Issues

**1. "Command not found: python3"**
```bash
# Ubuntu/Debian
sudo apt install python3 python3-pip

# CentOS/RHEL
sudo yum install python3 python3-pip

# Fedora
sudo dnf install python3 python3-pip
```

**2. "Module not found" errors**
```bash
pip install --upgrade pip
pip install -r requirements.txt --force-reinstall --no-cache-dir
```

**3. "Groq API Key not set" error**
```bash
# Check if set
echo $GROQ_API_KEY

# Set temporarily
export GROQ_API_KEY="your_api_key_here"

# Set permanently
echo 'export GROQ_API_KEY="your_api_key_here"' >> ~/.bashrc
source ~/.bashrc
```

**4. "Permission denied" errors**
```bash
chmod +x app.py
# or use sudo for system-level commands
```

**5. PyTorch installation issues**
```bash
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

**6. FAISS installation problems**
```bash
# Ubuntu/Debian
sudo apt install libfaiss-dev
pip install faiss-cpu --no-cache-dir

# CentOS/RHEL/Fedora
pip install faiss-cpu --no-cache-dir
```

**7. Build dependencies missing**
```bash
# Ubuntu/Debian
sudo apt install build-essential python3-dev

# CentOS/RHEL
sudo yum groupinstall "Development Tools"
sudo yum install python3-devel

# Fedora
sudo dnf groupinstall "Development Tools"
sudo dnf install python3-devel
```

### Performance Optimization
- **CPU Architecture**: Optimized for x86_64 and ARM64
- **Memory Management**: Efficient handling of large models
- **First run**: May be slower due to model downloads
- **Subsequent runs**: Faster as models are cached locally

### Linux Security Considerations
- **SELinux/AppArmor**: May require policy adjustments
- **Firewall**: Ensure outbound HTTPS access for API calls
- **User Permissions**: Some forensic commands require root privileges

## File Structure
```
dist_linux/
├── app.py                          # Main application (PyArmor protected)
├── requirements.txt                # Python dependencies
├── scrape_windows_cmd_docs.py     # Documentation scraper
├── pyarmor_runtime_000000/        # PyArmor runtime files
└── rag/                           # RAG system components
    ├── __init__.py
    ├── llamaindex_rag.py          # LlamaIndex RAG implementation
    └── [other RAG files]
```

## Linux Forensic Commands

### System Analysis
- **System Information**: `uname -a`, `lsb_release -a`, `hostnamectl`
- **Hardware Info**: `lscpu`, `lsmem`, `lsblk`, `lspci`, `lsusb`
- **Kernel Modules**: `lsmod`, `modinfo`
- **System Logs**: `journalctl`, `dmesg`, `/var/log/*`

### Network Forensics
- **Network Interfaces**: `ip addr show`, `ifconfig`
- **Routing Table**: `ip route show`, `netstat -rn`
- **Active Connections**: `ss -tuln`, `netstat -tuln`
- **Network Statistics**: `iftop`, `nethogs`, `tcpdump`

### Process Analysis
- **Process Tree**: `pstree`, `ps aux --forest`
- **System Calls**: `strace`, `ltrace`
- **Open Files**: `lsof`, `fuser`
- **Memory Analysis**: `pmap`, `/proc/*/maps`

### File System Forensics
- **File Permissions**: `ls -la`, `find / -perm -4000`
- **Disk Usage**: `df -h`, `du -sh`
- **File Systems**: `mount`, `findmnt`, `lsblk -f`
- **Extended Attributes**: `getfattr`, `setfattr`

### Security Analysis
- **User Accounts**: `/etc/passwd`, `/etc/shadow`, `lastlog`
- **Login History**: `last`, `lastb`, `who`, `w`
- **Sudo Logs**: `/var/log/auth.log`, `/var/log/secure`
- **Cron Jobs**: `crontab -l`, `/etc/crontab`, `/var/spool/cron/*`

## Security Notes
- ⚠️ **Ethical Use Only**: This tool is for authorized security testing
- 🔒 **API Key Security**: Never share your Groq API key
- 🛡️ **Command Review**: Always review commands before execution
- 📝 **Logging**: Commands and outputs may be logged for debugging
- 🐧 **Root Access**: Some commands may require sudo privileges
- 🔐 **SELinux/AppArmor**: Respect mandatory access controls

## Support & Updates

### Getting Help
- **Email**: ForensIQally@outlook.com
- **In-app**: Type `contact` for support information

### Updates
- Check the main site regularly for updates
- New versions may include additional forensic capabilities
- Update instructions will be provided with new releases

### Known Limitations
- Requires internet connection for AI generation
- Some system-level commands may need root privileges
- Performance depends on system specifications
- Distribution-specific commands may vary

## License & Legal
- This software is for educational and authorized security testing only
- Users are responsible for compliance with local laws and regulations
- PyArmor protection ensures code integrity and licensing compliance
- Respect system security policies and user privacy

---

**ForensIQshell v1.0 - Linux Edition**  
*Empowering Ethical Hackers with AI-Driven Command Intelligence*
