# 🖥️ Linux System Monitoring Guide

## 📊 Introduction to System Monitoring

Monitoring system resources is essential to ensure optimal performance, detect issues, and troubleshoot problems in Linux. Various tools allow us to monitor:

🔹 **CPU Usage**  
🔹 **Memory Consumption**  
🔹 **Disk I/O**  
🔹 **Network Activity**  
🔹 **Running Processes**

## 🔍 Index of Commands Covered

### 🧠 CPU and Memory Monitoring
| Command | Description |
|---------|-------------|
| `top` | Real-time system monitoring |
| `htop` | Interactive process viewer (requires installation) |
| `vmstat` | Report system performance statistics |
| `free -m` | Show memory usage |
### 💾 Disk Monitoring
| Command | Description |
|---------|-------------|
| `df -h` | Check disk space usage |
| `du -sh /path` | Show disk usage of a specific directory |
| `iostat` | Display CPU and disk I/O statistics |
### 🌐 Network Monitoring
| Command | Description |
|---------|-------------|
| `ifconfig` | Show network interfaces (deprecated, use ip a) |
| `ip a` | Show network interface details |
| `netstat -tulnp` | Show active connections and listening ports |
| `ss -tulnp` | Alternative to netstat for socket statistics |
| `ping hostname` | Test network connectivity |
| `traceroute hostname` | Show network path to a host |
| `nslookup domain` | Get DNS resolution details |
### 📜 Log Monitoring
| Command | Description |
|---------|-------------|
| `tail -f /var/log/syslog` | Live monitoring of system logs |
| `journalctl -f` | Live system logs for systemd-based distros |
| `dmesg | tail` | View kernel logs |
## 🚀 CPU and Memory Monitoring

### 🔄 Using top
```bash
top
# Press q to quit
```

### 🎨 Using htop (User-friendly alternative)
```bash
htop
# Use arrow keys to navigate
# F9 to kill processes
```

### 📊 Using vmstat
```bash
vmstat 1 5  # Update every 1 sec, show 5 updates
```

### 💾 Checking Memory Usage
```bash
free -m  # Shows memory in megabytes
```

## 💽 Disk Monitoring

### 📊 Using df
```bash
df -h  # Check disk space
```

### 📂 Using du
```bash
du -sh /var/log  # Directory size
```

### ⚡ Using iostat
```bash
iostat  # Disk and CPU stats
```
## 🌐 Network Monitoring

### 🔌 Checking Network Interfaces
```bash
ip a  # Show IP addresses
```

### 🚪 Viewing Open Ports
```bash
netstat -tulnp  # Listening ports
ss -tulnp       # Alternative
```

### 🛜 Testing Connectivity
```bash
ping google.com       # Test connection
traceroute google.com  # Trace path
```

### 🔎 Checking DNS
```bash
nslookup example.com  # DNS resolution
```
## 📜 Log Monitoring

### 🔍 Live System Logs
```bash
tail -f /var/log/syslog  # Follow logs
journalctl -f            # Systemd logs
```

### 🖥️ Kernel Logs
```bash
dmesg | tail  # View kernel logs
```