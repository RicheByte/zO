# ZO - AI-Powered CLI Assistant

![AI Assistant](https://img.shields.io/badge/AI-Powered-blue)
![CLI Tool](https://img.shields.io/badge/CLI-Tool-green)
![Security Research](https://img.shields.io/badge/Security-Research-red)
![License](https://img.shields.io/badge/License-MIT-yellow)

> **Intelligent command-line assistant for system administration and security research**  
> **Powered by Google's Gemini AI**

##  Overview

ZO is an intelligent CLI assistant that helps with system administration, cybersecurity research, and technical problem-solving. It provides AI-powered command suggestions, explanations, and guidance for various technical tasks, making complex operations more accessible and safer.

##  Features

-  **AI-Powered Assistance** - Integrated with Google's Gemini AI
-  **Natural Language Queries** - Ask questions in plain English
-  **Command Suggestions** - Get intelligent command recommendations with explanations
-  **Usage Dashboard** - Track your queries and command execution
-  **Secure API Storage** - Encrypted key storage using AES-256
-  **Interactive Execution** - Review and confirm commands before running
-  **Command History** - Keep track of executed commands
-  **Cross-Platform** - Works on Linux, macOS, and WSL

##  Installation

### Linux/macOS/WSL

1. **Clone the repository:**
```bash
git clone https://github.com/RicheByte/zo.git
cd zo
```

2. **Fix line endings (if coming from Windows):**
```bash
# Install dos2unix if needed
sudo apt-get install dos2unix  # Ubuntu/Debian
# or
sudo yum install dos2unix      # RedHat/CentOS

# Fix line endings
dos2unix zo/zo
```

3. **Install ZO:**
```bash
chmod +x zo/zo
sudo cp zo/zo /usr/local/bin/zo
```

4. **Verify installation:**
```bash
zo --help
```

###  Troubleshooting Installation

If you see `cannot execute: required file not found`, the file has Windows line endings:
```bash
# Fix with dos2unix
sudo dos2unix /usr/local/bin/zo

# OR fix with sed
sudo sed -i 's/\r$//' /usr/local/bin/zo

# Make executable
sudo chmod +x /usr/local/bin/zo
```

##  Initial Setup

### Step 1: Get Your API Key

1. Visit [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Sign in with your Google account
3. Click "Create API Key"
4. Copy your API key

### Step 2: Initialize ZO

```bash
zo init
```

Follow the prompts to:
- Enter your API key
- Verify the key is working
- Complete setup

Your API key will be encrypted and stored securely in `~/.zo/api_key`

##  Usage

### Basic Commands

```bash
# Get help
zo --help

# Ask questions
zo ask "what is nmap?"
zo ask "how to check open ports?"
zo ask "explain SSH security"

# Execute commands directly
zo execute "ls -la"
zo execute "pwd"
zo execute "whoami"

# View dashboard
zo status

# Reconfigure
zo reconfigure
```

###  Example Queries

#### Security Research
```bash
zo ask "what is a port scan?"
zo ask "explain common network scanning techniques"
zo ask "what are the most used nmap commands?"
zo ask "how does SSL/TLS encryption work?"
zo ask "what is a brute force attack?"
```

#### System Administration
```bash
zo ask "how to check disk usage in Linux?"
zo ask "show me how to manage systemd services"
zo ask "how to monitor system resources?"
zo ask "explain cron job syntax"
zo ask "how to check running processes?"
```

#### Networking
```bash
zo ask "how to troubleshoot network connectivity?"
zo ask "what is DNS and how does it work?"
zo ask "how to check which ports are listening?"
zo ask "explain TCP vs UDP"
```

#### Linux Commands
```bash
zo ask "how to find files in Linux?"
zo ask "explain grep command with examples"
zo ask "how to change file permissions?"
zo ask "what are Linux file system basics?"
```

##  Command Reference

| Command | Description |
|---------|-------------|
| `zo --help` | Display help and available commands |
| `zo init` | Initialize ZO with your API key (first-time setup) |
| `zo ask "question"` | Ask ZO about security, commands, or technical topics |
| `zo execute "command"` | Execute a shell command directly |
| `zo status` | Show dashboard with usage statistics |
| `zo reconfigure` | Reset and reconfigure API key |

##  How It Works

1. **Ask a Question** - ZO processes your query using Google's Gemini AI
2. **Get Intelligent Response** - Receive explanations and command suggestions
3. **Review Suggestions** - ZO shows you exactly what commands it recommends
4. **Execute Safely** - You confirm before any command runs
5. **Track History** - All interactions are logged for reference

##  Security Features

- **Encrypted Storage** - API keys encrypted with AES-256-CTR
- **User Confirmation** - Commands require explicit confirmation before execution
- **Command Logging** - Full audit trail in `~/.zo/logs`
- **Secure Permissions** - Config files set to user-only access (chmod 600)
- **No Auto-Execution** - You're always in control

##  Configuration Files

ZO stores its configuration in `~/.zo/`:

| File | Purpose |
|------|---------|
| `~/.zo/api_key` | Encrypted API key (AES-256) |
| `~/.zo/config` | Configuration settings |
| `~/.zo/logs` | Command execution logs |
| `~/.zo/history` | Command history |
| `~/.zo/dashboard.json` | Usage statistics |

##  Requirements

- **Bash** 4.0 or higher
- **curl** - For API communication
- **openssl** - For secure key encryption
- **Python 3** - For JSON processing (optional but recommended)
- **Google AI Studio API Key** - Free at [aistudio.google.com](https://aistudio.google.com/app/apikey)

##  Troubleshooting

### "cannot execute: required file not found"

This error means the file has Windows line endings (CRLF). Fix it:

```bash
# Method 1: Using dos2unix
sudo apt-get install dos2unix
sudo dos2unix /usr/local/bin/zo
sudo chmod +x /usr/local/bin/zo

# Method 2: Using sed
sudo sed -i 's/\r$//' /usr/local/bin/zo
sudo chmod +x /usr/local/bin/zo
```

### "Error: ZO not initialized"

Run the initialization:
```bash
zo init
```

### "Error: API key not found"

Reconfigure with a new API key:
```bash
zo reconfigure
```

### API Key Issues

If your API key isn't working:
1. Verify it's correct at [Google AI Studio](https://aistudio.google.com/app/apikey)
2. Check you copied the entire key
3. Run `zo reconfigure` and enter it again

### Permission Errors

If you get permission denied:
```bash
sudo chmod +x /usr/local/bin/zo
```

### Check Logs

For detailed error information:
```bash
cat ~/.zo/logs
```

##  Pro Tips

1. **Be Specific** - More detailed questions get better answers
   -  "network stuff"
   -  "how to scan for open ports on my local network?"

2. **Ask for Explanations** - ZO excels at teaching
   - "explain how SSH authentication works"
   - "what's the difference between TCP and UDP?"

3. **Request Examples** - Get practical command examples
   - "show me nmap examples for beginners"
   - "grep command examples for log analysis"

4. **Security First** - Always review commands before executing
   - Read what the command does
   - Understand the impact
   - Confirm it's safe for your system

5. **Use the Dashboard** - Track your usage
   ```bash
   zo status
   ```

##  Disclaimer

**For Educational and Authorized Use Only**

ZO is designed for:
- Learning about system administration
- Authorized security research
- Managing systems you own or have permission to manage

**NOT for:**
- Unauthorized access to systems
- Illegal activities
- Malicious purposes

Users are responsible for complying with all applicable laws and regulations. The developers are not responsible for misuse of this tool.

##  License

MIT License - See LICENSE file for details

##  Contributing

Contributions are welcome! Please feel free to submit pull requests or open issues for bugs and feature requests.

##  Support

- **Issues**: [GitHub Issues](https://github.com/RicheByte/zo/issues)
- **Documentation**: This README
- **API Key**: [Google AI Studio](https://aistudio.google.com/app/apikey)



