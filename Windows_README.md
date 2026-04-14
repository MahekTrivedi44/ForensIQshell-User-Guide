# ForensIQshell - Windows Distribution 🛡️

## Overview
ForensIQshell is an AI-powered forensic shell command assistant that helps cybersecurity professionals and ethical hackers generate accurate shell commands for Windows environments. It combines the power of Groq's LLM with a sophisticated RAG (Retrieval-Augmented Generation) system to provide context-aware command suggestions.

## Features
- 🤖 **AI-Powered Command Generation**: Uses Groq's Llama 3.1 model for intelligent command suggestions
- 📚 **RAG-Enhanced Context**: Leverages LlamaIndex with forensic documentation for better accuracy
- 🔍 **Windows-Specific**: Optimized for Windows CMD and PowerShell environments
- 🛡️ **Security-Focused**: Designed for ethical hacking and cybersecurity tasks
- ⚡ **Interactive Execution**: Step-by-step command confirmation and execution
- 🔒 **PyArmor Protected**: Source code is obfuscated for security

## System Requirements
- **Operating System**: Windows 10/11 (64-bit)
- **Python**: 3.8 or higher
- **Memory**: Minimum 4GB RAM (8GB recommended)
- **Storage**: At least 2GB free space
- **Internet**: Required for Groq API calls and initial setup

## Installation & Setup

### Step 1: Verify Python Installation
Open Command Prompt or PowerShell and check your Python version:
```cmd
python --version
```
If Python is not installed, download it from [python.org](https://python.org/downloads/)

### Step 2: Extract and Navigate
1. Extract the `dist_win` folder to your desired location
2. Open Command Prompt or PowerShell as Administrator
3. Navigate to the extracted folder:
```cmd
cd path\to\dist_win
```

### Step 3: Install Dependencies
Install all required Python packages:
```cmd
pip install -r requirements.txt
```

**Note**: This may take 5-10 minutes as it installs machine learning libraries including PyTorch.

### Step 4: Configure API Key
You need a Groq API key to use ForensIQshell:

1. Get your free API key from [Groq Console](https://console.groq.com/)
2. Set it as an environment variable:

**For Command Prompt:**
```cmd
set GROQ_API_KEY=your_api_key_here
```

**For PowerShell:**
```powershell
$env:GROQ_API_KEY="your_api_key_here"
```

**For permanent setup (recommended):**
1. Open System Properties → Advanced → Environment Variables
2. Add new system variable: `GROQ_API_KEY` with your API key value

## Running ForensIQshell

### Method 1: Command Prompt
```cmd
cd path\to\dist_win
python app.py
```

### Method 2: PowerShell
```powershell
cd path\to\dist_win
python app.py
```

### Method 3: Direct Execution
```cmd
python "C:\path\to\dist_win\app.py"
```

## Usage Guide

### Starting the Application
When you run ForensIQshell, you'll see:
```
Welcome to ForensIQshell 🛡️
Please keep checking the main site for updates.
For inquiries, feedback, or issues with the app, contact: ForensIQally@outlook.com
-----------------------------------------------------------------------------------
Detected environment: powershell (or cmd)
Loading documents from: data/powershell (or data/cmd)
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
🔍 Your forensic shell request: search for recently modified files in C:\Users
```

### Command Execution Flow
1. **Request**: Enter your forensic task in natural language
2. **Generation**: AI generates appropriate Windows commands
3. **Review**: Each command is displayed with explanation
4. **Confirmation**: Choose to execute (yes/no/all/skip-remaining)
5. **Execution**: Commands run in your shell environment
6. **Results**: View output and any errors

### Special Commands
- `exit` or `quit`: Close the application
- `contact`: Display support information

## Windows-Specific Features

### Shell Detection
ForensIQshell automatically detects whether you're running in:
- **Command Prompt (CMD)**: Uses `cmd.exe /C`
- **PowerShell**: Uses `powershell.exe -Command`

### Tool Installation
The AI can automatically install Windows tools using:
- **Winget**: Windows Package Manager
- **Chocolatey**: Third-party package manager
- **Direct downloads**: For specialized tools

### Path Management
For newly installed tools, ForensIQshell handles PATH issues by:
- Adding installation directories to current session PATH
- Using full executable paths when necessary
- Providing non-interactive installation flags

## Troubleshooting

### Common Issues

**1. "Module not found" errors**
```cmd
pip install --upgrade pip
pip install -r requirements.txt --force-reinstall
```

**2. "Groq API Key not set" error**
- Verify your API key is correctly set as environment variable
- Restart your terminal after setting the variable

**3. "Permission denied" errors**
- Run Command Prompt or PowerShell as Administrator
- Check Windows Defender/antivirus settings

**4. PyTorch installation issues**
```cmd
pip install torch --index-url https://download.pytorch.org/whl/cpu
```

**5. FAISS installation problems**
```cmd
pip install faiss-cpu --no-cache-dir
```

### Performance Optimization
- **First run**: May be slower due to model downloads
- **Subsequent runs**: Faster as models are cached locally
- **Memory usage**: Close other applications if experiencing slowdowns

### Windows Defender
If Windows Defender flags the application:
1. Add the `dist_win` folder to exclusions
2. This is normal for PyArmor-protected applications

## File Structure
```
dist_win/
├── app.py                          # Main application (PyArmor protected)
├── requirements.txt                # Python dependencies
├── scrape_windows_cmd_docs.py     # Documentation scraper
├── pyarmor_runtime_000000/        # PyArmor runtime files
└── rag/                           # RAG system components
    ├── __init__.py
    ├── llamaindex_rag.py          # LlamaIndex RAG implementation
    └── [other RAG files]
```

## Security Notes
- ⚠️ **Ethical Use Only**: This tool is for authorized security testing
- 🔒 **API Key Security**: Never share your Groq API key
- 🛡️ **Command Review**: Always review commands before execution
- 📝 **Logging**: Commands and outputs may be logged for debugging

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
- Some advanced tools may need manual installation
- Performance depends on system specifications

## License & Legal
- This software is for educational and authorized security testing only
- Users are responsible for compliance with local laws and regulations
- PyArmor protection ensures code integrity and licensing compliance

---

**ForensIQshell v1.0 - Windows Edition**  
*Empowering Ethical Hackers with AI-Driven Command Intelligence*
