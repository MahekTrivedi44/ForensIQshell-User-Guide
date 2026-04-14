# ForensIQshell - macOS Distribution 🛡️

## Overview
ForensIQshell is an AI-powered forensic shell command assistant that helps cybersecurity professionals and ethical hackers generate accurate shell commands for macOS environments. It combines the power of Groq's LLM with a sophisticated RAG (Retrieval-Augmented Generation) system to provide context-aware command suggestions.

## Features
- 🤖 **AI-Powered Command Generation**: Uses Groq's Llama 3.1 model for intelligent command suggestions
- 📚 **RAG-Enhanced Context**: Leverages LlamaIndex with forensic documentation for better accuracy
- 🍎 **macOS-Specific**: Optimized for macOS Terminal, Zsh, and Bash environments
- 🛡️ **Security-Focused**: Designed for ethical hacking and cybersecurity tasks
- ⚡ **Interactive Execution**: Step-by-step command confirmation and execution
- 🔒 **PyArmor Protected**: Source code is obfuscated for security

## System Requirements
- **Operating System**: macOS 10.15 (Catalina) or later
- **Python**: 3.8 or higher
- **Memory**: Minimum 4GB RAM (8GB recommended)
- **Storage**: At least 2GB free space
- **Internet**: Required for Groq API calls and initial setup
- **Xcode Command Line Tools**: Required for some dependencies

## Installation & Setup

### Step 1: Install Xcode Command Line Tools
Open Terminal and run:
```bash
xcode-select --install
```

### Step 2: Verify Python Installation
Check your Python version:
```bash
python3 --version
```
If Python is not installed, install it via Homebrew:
```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
brew install python
```

### Step 3: Extract and Navigate
1. Extract the `dist_mac` folder to your desired location
2. Open Terminal
3. Navigate to the extracted folder:
```bash
cd /path/to/dist_mac
```

### Step 4: Create Virtual Environment (Recommended)
```bash
python3 -m venv forensiq_env
source forensiq_env/bin/activate
```

### Step 5: Install Dependencies
Install all required Python packages:
```bash
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
Add to your shell profile (`~/.zshrc` for Zsh or `~/.bash_profile` for Bash):
```bash
echo 'export GROQ_API_KEY="your_api_key_here"' >> ~/.zshrc
source ~/.zshrc
```

## Running ForensIQshell

### Method 1: With Virtual Environment
```bash
cd /path/to/dist_mac
source forensiq_env/bin/activate
python3 app.py
```

### Method 2: Direct Execution
```bash
cd /path/to/dist_mac
python3 app.py
```

### Method 3: Make Executable (Optional)
```bash
chmod +x app.py
./app.py
```

## Usage Guide

### Starting the Application
When you run ForensIQshell, you'll see:
```
Welcome to ForensIQshell 🛡️
Please keep checking the main site for updates.
For inquiries, feedback, or issues with the app, contact: ForensIQally@outlook.com
-----------------------------------------------------------------------------------
Detected environment: mac
Loading documents from: data/mac
RAG system initialized successfully!
Type 'exit' or 'quit' to stop, or 'contact' for support information.

🔍 Your forensic shell request:
```

### Example Commands
Try these example requests:

**Network Analysis:**
```
🔍 Your forensic shell request: scan all open ports on 192.168.1.1
```

**System Information:**
```
🔍 Your forensic shell request: get detailed system information including hardware specs
```

**Process Investigation:**
```
🔍 Your forensic shell request: find all running processes with network connections
```

**File Analysis:**
```
🔍 Your forensic shell request: search for recently modified files in /Users
```

**macOS Specific:**
```
🔍 Your forensic shell request: check system integrity protection status
🔍 Your forensic shell request: analyze system logs for security events
🔍 Your forensic shell request: list all installed applications
```

### Command Execution Flow
1. **Request**: Enter your forensic task in natural language
2. **Generation**: AI generates appropriate macOS commands
3. **Review**: Each command is displayed with explanation
4. **Confirmation**: Choose to execute (yes/no/all/skip-remaining)
5. **Execution**: Commands run in your Terminal environment
6. **Results**: View output and any errors

### Special Commands
- `exit` or `quit`: Close the application
- `contact`: Display support information

## macOS-Specific Features

### Shell Detection
ForensIQshell automatically detects and works with:
- **Zsh**: Default shell in macOS Catalina and later
- **Bash**: Legacy shell (still supported)
- **Other shells**: Fish, tcsh, etc.

### Tool Installation
The AI can automatically install macOS tools using:
- **Homebrew**: Primary package manager for macOS
- **MacPorts**: Alternative package manager
- **Direct downloads**: For specialized tools
- **App Store**: For GUI applications

### Security Integration
- **System Integrity Protection (SIP)**: Respects macOS security features
- **Gatekeeper**: Works with macOS app security
- **Keychain**: Can interact with macOS keychain for credentials
- **Code Signing**: Understands macOS code signing requirements

## Troubleshooting

### Common Issues

**1. "Command not found: python3"**
```bash
brew install python
# or
python --version  # Try python instead of python3
```

**2. "Module not found" errors**
```bash
pip install --upgrade pip
pip install -r requirements.txt --force-reinstall
```

**3. "Groq API Key not set" error**
- Verify your API key is correctly set as environment variable
- Restart Terminal after setting the variable
- Check with: `echo $GROQ_API_KEY`

**4. "Permission denied" errors**
```bash
sudo chmod +x app.py
# or run with sudo if needed for system-level commands
```

**5. PyTorch installation issues on Apple Silicon**
```bash
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

**6. FAISS installation problems**
```bash
brew install faiss
pip install faiss-cpu --no-cache-dir
```

**7. Xcode Command Line Tools issues**
```bash
sudo xcode-select --reset
xcode-select --install
```

### Performance Optimization
- **Apple Silicon (M1/M2)**: Optimized performance with native libraries
- **Intel Macs**: Full compatibility with x86_64 libraries
- **First run**: May be slower due to model downloads
- **Subsequent runs**: Faster as models are cached locally

### macOS Security Prompts
- **Gatekeeper warnings**: Click "Open Anyway" in System Preferences → Security & Privacy
- **Network access**: Allow Terminal network access when prompted
- **Full Disk Access**: May be needed for some forensic commands

## File Structure
```
dist_mac/
├── app.py                          # Main application (PyArmor protected)
├── requirements.txt                # Python dependencies
├── scrape_windows_cmd_docs.py     # Documentation scraper
├── pyarmor_runtime_000000/        # PyArmor runtime files
└── rag/                           # RAG system components
    ├── __init__.py
    ├── llamaindex_rag.py          # LlamaIndex RAG implementation
    └── [other RAG files]
```

## macOS-Specific Commands

### System Analysis
- **System Information**: `system_profiler SPHardwareDataType`
- **Security Status**: `csrutil status` (SIP status)
- **Installed Software**: `pkgutil --packages`
- **System Logs**: `log show --predicate 'category == "security"'`

### Network Forensics
- **Network Interfaces**: `ifconfig -a`
- **Routing Table**: `netstat -rn`
- **Active Connections**: `lsof -i`
- **WiFi Information**: `airport -I`

### File System Analysis
- **File Permissions**: `ls -la@e` (with extended attributes)
- **Disk Usage**: `du -sh *`
- **File System Info**: `diskutil list`
- **Spotlight Search**: `mdfind "query"`

## Security Notes
- ⚠️ **Ethical Use Only**: This tool is for authorized security testing
- 🔒 **API Key Security**: Never share your Groq API key
- 🛡️ **Command Review**: Always review commands before execution
- 📝 **Logging**: Commands and outputs may be logged for debugging
- 🍎 **SIP Compliance**: Respects System Integrity Protection

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
- Some system-level commands may need sudo privileges
- Performance depends on system specifications
- SIP may restrict certain forensic operations

## License & Legal
- This software is for educational and authorized security testing only
- Users are responsible for compliance with local laws and regulations
- PyArmor protection ensures code integrity and licensing compliance
- Respect macOS security features and user privacy

---

**ForensIQshell v1.0 - macOS Edition**  
*Empowering Ethical Hackers with AI-Driven Command Intelligence*
