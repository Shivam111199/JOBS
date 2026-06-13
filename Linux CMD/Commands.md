
LINUX COMMANDS

| Command       | Short Meaning                                 |
| ------------- | --------------------------------------------- |
| `top`         | Real-time CPU, memory, and process monitoring |
| `free -h`     | Check RAM and swap usage                      |
| `df -h`       | Check disk space usage                        |
| `df -i`       | Check inode usage                             |
| `du -sh`      | Check directory/file size                     |
| `ps -ef`      | List all running processes                    |
| `ps aux`      | Detailed process information                  |
| `pgrep`       | Find PID by process name                      |
| `kill PID`    | Gracefully terminate a process (SIGTERM)      |
| `kill -9 PID` | Forcefully terminate a process (SIGKILL)      |
| `vmstat`      | CPU, memory, swap, and process statistics     |
| `mpstat`      | CPU usage per processor/core                  |
| `ip a`        | Show IP addresses and network interfaces      |
| `ip route`    | Show routing table and default gateway        |
| `ping`        | Test network connectivity                     |
| `nslookup`    | Resolve hostname to IP using DNS              |
| `dig`         | Detailed DNS lookup                           |
| `curl`        | Test HTTP/HTTPS connectivity and APIs         |
| `ss -tulpn`   | Show listening ports and associated processes |
| `lsof -i`     | Show process using a network port             |
| `tcpdump`     | Capture and analyze network packets           |
| `grep`        | Search text or patterns in files              |
| `awk`         | Extract and process columns of text           |
| `sort`        | Sort data alphabetically or numerically       |
| `chmod`       | Change file/directory permissions             |
| `chown`       | Change file/directory owner                   |
| `systemctl`   | Manage and check system services              |
| `journalctl`  | View systemd service and system logs          |

### Quick Troubleshooting Mapping

| Problem                      | First Command        |
| ---------------------------- | -------------------- |
| CPU High                     | `top`                |
| Memory High                  | `free -h`            |
| Disk Full                    | `df -h`              |
| No Space but Disk Looks Fine | `df -i`              |
| Large Directory              | `du -sh`             |
| Find Process                 | `ps -ef` / `pgrep`   |
| Kill Process                 | `kill` / `kill -9`   |
| Service Down                 | `systemctl status`   |
| Check Logs                   | `journalctl`         |
| Network Issue                | `ping`               |
| DNS Issue                    | `nslookup` / `dig`   |
| Port Not Accessible          | `ss -tulpn`          |
| Who Uses Port 8080?          | `lsof -i :8080`      |
| API Not Working              | `curl`               |
| Packet-Level Investigation   | `tcpdump`            |
| Search Errors in Logs        | `grep ERROR logfile` |
| Extract Specific Column      | `awk '{print $1}'`   |

### 30-Second Interview Summary

```text
top         → CPU/Memory/Processes
free -h     → Memory
df -h       → Disk
df -i       → Inodes
du -sh      → Directory Size
ps/pgrep    → Processes
kill        → Stop Process
vmstat      → System Performance
mpstat      → Per-Core CPU
ip a        → IP Address
ip route    → Gateway/Route
ping        → Connectivity
nslookup    → DNS
curl        → HTTP/API Test
ss/lsof     → Ports & Connections
tcpdump     → Packet Capture
grep        → Search
awk         → Column Extraction
sort        → Sorting
chmod       → Permissions
chown       → Ownership
systemctl   → Services
journalctl  → Logs
```




This is a great idea for interview revision. Keep this as your **Linux Quick Reference Sheet**.

# 1. System Health & Performance

| Command         | Purpose                                   |
| --------------- | ----------------------------------------- |
| `uptime`        | Check uptime and load average             |
| `top`           | Real-time CPU, memory, process monitoring |
| `top -c`        | Show full process command line            |
| `htop`          | Interactive process viewer                |
| `free -h`       | Memory and swap usage                     |
| `vmstat 1`      | CPU, memory, swap, run queue statistics   |
| `mpstat -P ALL` | CPU usage per core                        |
| `sar -u`        | Historical CPU usage                      |
| `sar -r`        | Historical memory usage                   |
| `iostat -c`     | CPU statistics                            |
| `lscpu`         | CPU architecture information              |
| `nproc`         | Number of CPUs                            |
| `hostnamectl`   | System information                        |

---

# 2. Process Management

| Command               | Purpose                        |
| --------------------- | ------------------------------ |
| `ps -ef`              | List all processes             |
| `ps aux`              | Detailed process information   |
| `ps aux --sort=-%cpu` | Top CPU consumers              |
| `ps aux --sort=-%mem` | Top memory consumers           |
| `pgrep process`       | Find PID by process name       |
| `pgrep -fa process`   | Find process with full command |
| `pstree -p`           | Process hierarchy              |
| `kill PID`            | Gracefully stop process        |
| `kill -9 PID`         | Force kill process             |
| `pkill process`       | Kill by process name           |
| `killall process`     | Kill all matching processes    |
| `renice`              | Change process priority        |
| `top -H -p PID`       | Thread-level CPU usage         |
| `lsof -p PID`         | Files opened by process        |
| `ps -fp PID`          | Detailed process info          |

---

# 3. CPU Troubleshooting

| Command                | Purpose                 |
| ---------------------- | ----------------------- |
| `top`                  | CPU utilization         |
| `mpstat -P ALL`        | CPU per core            |
| `vmstat 1`             | Run queue and CPU waits |
| `uptime`               | Load average            |
| `ps aux --sort=-%cpu`  | High CPU process        |
| `top -H -p PID`        | High CPU thread         |
| `taskset -cp PID`      | CPU affinity            |
| `cat /proc/interrupts` | Hardware interrupts     |

---

# 4. Memory Troubleshooting

| Command                                  | Purpose                  |
| ---------------------------------------- | ------------------------ |
| `free -h`                                | Memory usage             |
| `top`                                    | Memory usage             |
| `vmstat 1`                               | Memory and swap stats    |
| `cat /proc/meminfo`                      | Detailed memory info     |
| `swapon -s`                              | Swap usage               |
| `pmap -x PID`                            | Process memory map       |
| `smem -rs rss`                           | Sort by actual RAM usage |
| `dmesg -T \| grep -i oom`                | Check OOM events         |
| `journalctl -k \| grep -i oom`           | OOM logs                 |
| `watch -n 5 'ps -p PID -o rss,vsz,%mem'` | Memory leak monitoring   |

### Memory Terms

| Term       | Meaning                                    |
| ---------- | ------------------------------------------ |
| RSS        | Actual RAM used                            |
| VSZ        | Virtual memory allocated                   |
| Swap       | Disk used as memory                        |
| OOM Killer | Kernel kills process when memory exhausted |

---

# 5. Disk Space Troubleshooting

| Command                    | Purpose             |
| -------------------------- | ------------------- |
| `df -h`                    | Filesystem usage    |
| `du -sh *`                 | Directory size      |
| `du -sh /var/*`            | Large directories   |
| `find / -type f -size +1G` | Large files         |
| `lsblk`                    | Disk layout         |
| `fdisk -l`                 | Disk partitions     |
| `mount`                    | Mounted filesystems |

---

# 6. Inode Troubleshooting

| Command                      | Purpose               |
| ---------------------------- | --------------------- |
| `df -i`                      | Inode usage           |
| `ls -i`                      | Display inode numbers |
| `find /var -type f \| wc -l` | Count files           |
| `find / -xdev -type f`       | Find inode consumers  |

### Inode Terms

| Term  | Meaning             |
| ----- | ------------------- |
| Inode | Metadata for a file |
| IUsed | Used inodes         |
| IFree | Available inodes    |
| IUse% | Inode utilization   |

---

# 7. Network Troubleshooting

| Command                | Purpose                |
| ---------------------- | ---------------------- |
| `ip a`                 | Show IP addresses      |
| `ip route`             | Routing table          |
| `ip neigh`             | ARP table              |
| `ping host`            | Connectivity test      |
| `traceroute host`      | Network path           |
| `nslookup host`        | DNS lookup             |
| `dig host`             | DNS details            |
| `cat /etc/resolv.conf` | DNS server config      |
| `curl -I URL`          | HTTP headers           |
| `curl -v URL`          | Detailed HTTP request  |
| `wget URL`             | Download file          |
| `tcpdump`              | Packet capture         |
| `ss -tulpn`            | Listening ports        |
| `ss -ant`              | Active TCP connections |
| `lsof -i`              | Process using port     |
| `nc -zv host port`     | Test port connectivity |
| `telnet host port`     | Test port connectivity |

---

# 8. Firewall Troubleshooting

| Command                      | Purpose                |
| ---------------------------- | ---------------------- |
| `iptables -L -n`             | List firewall rules    |
| `iptables -L -n -v`          | Firewall with counters |
| `iptables -L --line-numbers` | Show rule numbers      |
| `firewall-cmd --list-all`    | Firewalld rules        |
| `iptables -D INPUT N`        | Delete firewall rule   |

---

# 9. Log Analysis

| Command                  | Purpose                 |
| ------------------------ | ----------------------- |
| `tail -f file.log`       | Live log monitoring     |
| `tail -100 file.log`     | Last 100 lines          |
| `head file.log`          | First 10 lines          |
| `less file.log`          | Scroll through file     |
| `grep ERROR file.log`    | Search text             |
| `grep -i error file.log` | Case-insensitive search |
| `grep -r text dir/`      | Recursive search        |
| `journalctl -u service`  | Service logs            |
| `journalctl -xe`         | System logs             |
| `dmesg`                  | Kernel logs             |

---

# 10. Text Processing (Most Asked)

## grep

| Command          | Purpose          |
| ---------------- | ---------------- |
| `grep text file` | Search text      |
| `grep -i`        | Ignore case      |
| `grep -v`        | Exclude match    |
| `grep -c`        | Count matches    |
| `grep -n`        | Show line number |
| `grep -r`        | Recursive search |

---

## awk

| Command                           | Purpose      |
| --------------------------------- | ------------ |
| `awk '{print $1}' file`           | First column |
| `awk '{print $NF}' file`          | Last column  |
| `awk '/ERROR/' file`              | Filter lines |
| `awk '{sum+=$1} END {print sum}'` | Sum column   |

Example:

```bash id="p1phhu"
df -h | awk '{print $5}'
```

Prints usage column.

---

## sort

| Command     | Purpose             |
| ----------- | ------------------- |
| `sort file` | Sort alphabetically |
| `sort -n`   | Numeric sort        |
| `sort -r`   | Reverse sort        |
| `sort -u`   | Unique sort         |

---

## uniq

| Command   | Purpose           |
| --------- | ----------------- |
| `uniq`    | Remove duplicates |
| `uniq -c` | Count duplicates  |

Example:

```bash id="gtl4d9"
sort file | uniq -c
```

---

## cut

| Command                  | Purpose        |
| ------------------------ | -------------- |
| `cut -d',' -f1 file.csv` | Extract column |

---

## sed

| Command                  | Purpose          |
| ------------------------ | ---------------- |
| `sed 's/old/new/g' file` | Replace text     |
| `sed -n '1,10p' file`    | Print lines 1-10 |

---

# 11. File & Permission Commands

| Command   | Purpose           |
| --------- | ----------------- |
| `ls -ltr` | List files        |
| `pwd`     | Current directory |
| `cd`      | Change directory  |
| `mkdir`   | Create directory  |
| `touch`   | Create file       |
| `cp`      | Copy              |
| `mv`      | Move/Rename       |
| `rm -rf`  | Delete            |
| `cat`     | Display file      |
| `less`    | View file         |

---

# 12. Permissions

| Command                 | Purpose                       |
| ----------------------- | ----------------------------- |
| `chmod 755 file`        | Change permissions            |
| `chmod 644 file`        | Read/write owner, read others |
| `chown user file`       | Change owner                  |
| `chown user:group file` | Change owner and group        |
| `umask`                 | Default permissions           |

### Common Permission Values

| Value | Meaning                         |
| ----- | ------------------------------- |
| 777   | Full access                     |
| 755   | Owner full, others read/execute |
| 644   | Owner write, others read        |
| 600   | Owner only                      |

---

# 13. Service Management

| Command                     | Purpose         |
| --------------------------- | --------------- |
| `systemctl status service`  | Check service   |
| `systemctl start service`   | Start service   |
| `systemctl stop service`    | Stop service    |
| `systemctl restart service` | Restart service |
| `systemctl enable service`  | Start at boot   |
| `systemctl disable service` | Disable at boot |















Memorizing just these one-line meanings is usually enough to answer the first round of Linux troubleshooting questions.
