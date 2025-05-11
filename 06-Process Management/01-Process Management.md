<div align="center">
  <img src="https://img.shields.io/badge/Linux-Process%20Management-blue" alt="Process Management" />
  <img src="https://img.shields.io/badge/System-Monitoring-green" alt="Monitoring" />
  <img src="https://img.shields.io/badge/Performance-Optimization-orange" alt="Optimization" />
</div>

# 🔄 Linux Process Management Guide
## 🚀 Introduction
A process is an instance of a running program. Linux provides multiple utilities to monitor, manage, and control processes effectively. Each process has a unique Process ID (PID) and belongs to a parent process.

## 📋 Table of Contents
1. [Viewing Processes](#-viewing-processes)
2. [Managing Processes](#-managing-processes)
3. [Background & Foreground](#-background--foreground-processes)
4. [Monitoring](#-monitoring-system-processes)
5. [Daemon Management](#-daemon-process-management)

---

## 👀 Viewing Processes
| Command | Description | Example |
|---------|-------------|---------|
| `ps aux` | View all running processes | `ps aux` |
| `ps -u username` | View processes for a specific user | `ps -u root` |
| `ps -C processname` | Show a process by name | `ps -C nginx` |
| `pgrep processname` | Find PID by name | `pgrep nginx` |
| `pidof processname` | Find PID of running program | `pidof nginx` |
## ⚙️ Managing Processes
| Command | Description | Example |
|---------|-------------|---------|
| `kill PID` | Terminate a process by PID | `kill 1234` |
| `pkill processname` | Terminate by name | `pkill nginx` |
| `kill -9 PID` | Force kill a process | `kill -9 1234` |
| `pkill -9 processname` | Kill all instances | `pkill -9 nginx` |
| `kill -STOP PID` | Stop a running process | `kill -STOP 1234` |
| `kill -CONT PID` | Resume stopped process | `kill -CONT 1234` |
| `renice -n 10 -p PID` | Lower priority | `renice -n 10 -p 1234` |
| `renice -n -5 -p PID` | Increase priority (root) | `sudo renice -n -5 -p 1234` |
## 🔄 Background & Foreground Processes
| Command | Description | Example |
|---------|-------------|---------|
| `command &` | Run in background | `sleep 60 &` |
| `jobs` | List background jobs | `jobs` |
| `fg %jobnumber` | Bring to foreground | `fg %1` |
| `Ctrl+Z` | Suspend process | (keyboard shortcut) |
| `bg %jobnumber` | Resume in background | `bg %1` |
## 📊 Monitoring System Processes
| Command | Description | Example |
|---------|-------------|---------|
| `top` | Interactive process viewer | `top` |
| `htop` | Enhanced process viewer | `htop` (requires install) |
| `nice -n 10 command` | Run with lower priority | `nice -n 10 ./script.sh` |
| `renice -n -5 -p PID` | Increase priority (root) | `sudo renice -n -5 -p 1234` |
## 👻 Daemon Process Management
| Command | Description | Example |
|---------|-------------|---------|
| `systemctl list-units --type=service` | List all daemons | `systemctl list-units --type=service` |
| `systemctl start service-name` | Start a service | `systemctl start nginx` |
| `systemctl stop service-name` | Stop a service | `systemctl stop nginx` |
| `systemctl enable service-name` | Enable at startup | `systemctl enable nginx` |
## 🔍 Detailed Command Examples
### 📊 Using ps
```bash
# Show processes for a specific user
ps -u username

# Show a process by name
ps -C processname
```

### 🔎 Using pgrep
```bash
# Find a process by name and return its PID
pgrep processname
```

### 🔢 Using pidof
```bash
# Find the PID of a running program
pidof processname
```
### ☠️ Killing Processes
```bash
# Terminate a process by PID
kill PID

# Terminate using process name
pkill processname

# Force kill a process
kill -9 PID

# Kill all instances of a process
pkill -9 processname
```
### ⏸️ Stopping & Resuming Processes
```bash
# Stop a running process
kill -STOP PID

# Resume a stopped process
kill -CONT PID
```
### ⚖️ Changing Process Priority
```bash
# View process priorities
top  # Look at the NI column

# Change priority of a running process
renice -n 10 -p PID  # Lower priority (positive values)
renice -n -5 -p PID  # Higher priority (negative values, root required)
```
### 🔄 Running Processes in Background
```bash
# Run a command in background
command &

# List background jobs
jobs

# Bring job to foreground
fg %jobnumber

# Keyboard shortcut to suspend process
Ctrl+Z

# Resume suspended process in background
bg %jobnumber
```
### 📈 Monitoring System Processes
```bash
# Using top (interactive)
top
# Press k to kill, r to renice, q to quit

# Using htop (enhanced)
htop

# Run command with specific priority
nice -n 10 command

# Change priority of existing process
renice -n -5 -p PID
```
### 👻 Daemon Processes
```bash
# List all system daemons
systemctl list-units --type=service

# Start a daemon
systemctl start service-name

# Stop a daemon
systemctl stop service-name

# Enable service at startup
systemctl enable service-name
```
## 🎯 Conclusion
Process management is crucial for system performance and stability. By mastering tools like:
- `ps`, `top`, `htop` for monitoring
- `kill`, `pkill` for process control
- `nice`, `renice` for priority management

You can efficiently control and optimize your Linux system's processes.