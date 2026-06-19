# Linux CLI Quick Revision Notes

---

### Shell Definition
Shell is a command-line interpreter that takes user commands and communicates with the Operating System Kernel.
`echo $SHELL` {GPT Added}

**Flow:**  
User $\rightarrow$ Shell $\rightarrow$ Kernel $\rightarrow$ Hardware

---

### Paths & Wildcards

| Symbol | Meaning |
| :--- | :--- |
| `.` | Current Directory |
| `..` | Parent Directory |
| `~` | Home Directory |
| `-` | Previous Directory |
| `*` | Matches multiple characters |
| `?` | Matches single character |

#### Absolute vs Relative Path

| Absolute Path | Relative Path |
| :--- | :--- |
| Starts from root `/` | Starts from current directory |
| Full path | Partial path |
| **Example:** `/home/user/docs` | **Example:** `docs/file.txt` |

---

### Bread & Butter Commands

| Command | Purpose | Example |
| :--- | :--- | :--- |
| `pwd` | Print current directory | `pwd` |
| `cd` | Change directory | `cd folder` |
| `mkdir` | Create directory | `mkdir test` |
| `touch` | Create file | `touch a.txt` |
| `ls` | List files | `ls -la` |
| `cp` | Copy files | `cp a.txt b.txt` |
| `mv` | Move/Rename | `mv a.txt b.txt` |
| `rm` | Delete files | `rm file.txt` |
| `cat` | Display file | `cat file.txt` |
| `less` | View file page by page | `less file.txt` |
| `more` | Basic pager | `more file.txt` |
| `tail` | Last lines of file | `tail -n 20 file.txt` |
| `tree` | Directory structure | `tree` |
| `wc` | Count lines/words/chars | `wc file.txt` |
| `date` | Show date/time | `date` |
| `man` | Manual page | `man grep` |
| `sudo` | Run as root | `sudo apt update` |
| `apt` | Package manager | `sudo apt install tree` |
| `rsync` | Fast file sync/copy | `rsync -av src dest` |

---

### Important Flags

#### `ls` Flags

| Flag | Meaning |
| :--- | :--- |
| `-l` | Long format |
| `-a` | Hidden files |
| `-h` | Human readable |
| `-t` | Sort by time |
| `-r` | Reverse order |
* **Example:** `ls -alhtr`

#### `cp` Flags

| Flag | Meaning |
| :--- | :--- |
| `-r` | Recursive copy |
| `-v` | Verbose |
* **Example:** `cp -r folder backup`

#### `rm` Flags

| Flag | Meaning |
| :--- | :--- |
| `-r` | Recursive delete |
| `-f` | Force delete |
* **Example:** `rm -rf folder`

---

### Permissions

#### `chmod`
* **Definition:** Changes file permissions.
* **Example:** `chmod 755 file.sh`

#### Permission Elements

| Number | Binary | Permission |
| :--- | :--- | :--- |
| **7** | `111` | `rwx` |
| **6** | `110` | `rw-` |
| **5** | `101` | `r-x` |
| **4** | `100` | `r--` |

#### Permission Groups

| Symbol | Meaning |
| :--- | :--- |
| `u` | User |
| `g` | Group |
| `o` | Others |

#### `chown`
* **Definition:** Changes file owner.
* **Example:** `sudo chown user file.txt`

---

### Process Commands

| Command | Purpose | Common Usage |
| :--- | :--- | :--- |
| `ps` | Snapshot of running processes | `ps -ef` |
| `top` | Live process monitoring | `top` |
| `kill` | Stop process | `kill -9 PID` |
| `free` | Memory usage | `free -h` |
| `df` | Disk usage | `df -h` |
| `uname` | System info | `uname -a` |
| `lspci` | Hardware devices | `lspci` |

#### `kill` Signals

| Signal | Meaning |
| :--- | :--- |
| `-1` | Reload |
| `-2` | Interrupt |
| `-9` | Force Kill |
| `-15` | Graceful Kill (Default) |

* **Why `kill -9`?** Forcefully terminates a process when it is not responding.

#### `top` vs `ps`

| `top` | `ps` |
| :--- | :--- |
| Live monitoring | Snapshot |
| Continuously updates | Runs once |
| Interactive | Non-interactive |

---

### Network Commands

| Command | Purpose | Examples |
| :--- | :--- | :--- |
| `ping` | Check connectivity | `ping google.com` |
| `ifconfig` | Network info | `ifconfig` |
| `ssh` | Remote login | `ssh user@host` |
| `netstat` | Connections & ports | `netstat` |
| `lsof` | Open files/ports | `lsof -i :5432` |
| `curl` | Download/Test APIs | `curl https://google.com` |
| `wget` | Download files | `wget URL` |

---

### Bash Utilities

| Command | Purpose |
| :--- | :--- |
| `grep` | Search text |
| `find` | Find files |
| `sort` | Sort lines |
| `awk` | Text processing |
| `sed` | Text editing |
| `xargs` | Build command arguments |
| `printenv` | Environment variables |
| `nano` | Terminal editor |

#### `grep`
* `grep word file.txt`
* `grep -i word file.txt`
* `grep -c word file.txt`
* `grep -r word folder`

| Flag | Meaning |
| :--- | :--- |
| `-i` | Ignore case |
| `-c` | Count |
| `-r` | Recursive |
| `-n` | Line number |

#### `find`
* `find . -name "*.txt"`
* `find . -type f`
* `find . -type d`

| Flag | Meaning |
| :--- | :--- |
| `-name` | Search by name |
| `-type f` | File |
| `-type d` | Directory |

#### `sort`
* `sort file.txt`
* `sort -r file.txt`
* `sort -n file.txt`

#### `awk`
* `awk '{print $1}' file.txt`  
  *(Prints first column)*

#### `sed`
* `sed 's/old/new/g' file.txt`  
  *(Replace text)*

#### Pipe Operator
* `cat file.txt | grep error`  
  *(Output of first command becomes input of second command)*

---

### Terminal Controls

| Shortcut | Action |
| :--- | :--- |
| **Ctrl+C** | Stop process |
| **Ctrl+Z** | Suspend process |
| **Ctrl+D** | EOF / Exit shell |
| **Ctrl+R** | Reverse search |
| **Tab** | Auto-complete |
| **↑ ↓** | Command history |

#### **Ctrl+C vs Ctrl+Z**
* **Ctrl+C:** Terminates process
* **Ctrl+Z:** Suspends process

---

### Frequently Asked Review Questions

* **Check Disk Status:** `df -h`
* **Most Senior Parent Process:** `ps -p 1` *(PID 1 is usually init/systemd)*
* **Computer Architecture:** `uname -m`
* **Audio Driver:**
  * *Linux:* `lspci | grep Audio`
  * *Mac:* `system_profiler SPAudioDataType`
* **Local IP Address:** `ifconfig`
* **Google IP:** `ping google.com`
* **Check Internet:** `ping google.com`
* **Node Location:** `which node`
* **VS Code Location:** `which code`
* **Browser PIDs:** `ps -ef | grep firefox`
* **Stop Browser:** `kill PID`
* **Top 3 CPU Processes:** `ps aux --sort=-%cpu | head -4`
* **Top 3 Memory Processes:** `ps aux --sort=-%mem | head -4`
* **Python Server Port 8000:** `python3 -m http.server 8000` *(Stop: Ctrl+C)*
* **Python Server Port 90:** `sudo python3 -m http.server 90`
* **Active Connections:** `netstat -tulpn`
* **PID Listening on Port 5432:** `lsof -i :5432`
* **Lines 100-200:** `head -200 book.txt | tail -101`
* **Delete All .log Files:** `find . -name "*.log" -delete`

---

### Service vs Application

| Service | Application |
| :--- | :--- |
| Runs in background | User interacts directly |
| Starts with system | Opened manually |
| **Example:** `nginx` | **Example:** `Firefox` |

---

### Revision Keywords
* **Shell** = Command Interpreter
* **chmod** = Change Permission
* **chown** = Change Owner
* **grep** = Search Text
* **find** = Search Files
* **ps** = Process Snapshot
* **top** = Live Monitoring
* **kill** = Send Signal
* **df** = Disk Usage
* **free** = Memory Usage
* **ifconfig** = Network Info
* **ssh** = Remote Access
* **awk** = Text Processing
* **sed** = Text Replacement
* **xargs** = Build Arguments
* **pipe** = Connect Commands
