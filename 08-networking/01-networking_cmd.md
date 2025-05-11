# 🌐 Linux Networking Commands Guide

## 🔌 Network Connectivity
### 🏓 Ping Test
```bash
ping google.com          # Basic connectivity test
ping -c 4 google.com     # Send 4 packets
ping -i 0.5 google.com  # Set interval to 0.5 seconds
```

## 🔍 Network Configuration
### 📡 Interface Information
```bash
ip a                     # Show all interfaces (modern)
ifconfig                 # Legacy interface info (deprecated)
ip addr show eth0        # Show specific interface
```

## 🚪 Network Connections
### 🕵️‍♂️ Active Connections
```bash
netstat -tulnp           # Show listening ports
netstat -tup            # Show active TCP connections
ss -tulnp               # Modern alternative to netstat
```

## 🌍 Web Tools
### 📥 Downloading Files
```bash
wget https://example.com/file.zip  # Basic download
wget -c https://example.com/file.zip  # Resume interrupted download
wget --limit-rate=200k https://example.com/file.zip  # Limit speed
```

### 🌐 Web Requests
```bash
curl https://example.com          # Fetch webpage
curl -I https://example.com       # Show headers only
curl -o output.html https://example.com  # Save to file
```

## 🛠️ Troubleshooting Tips
- If `ping` fails, check:
  - Network cable connection
  - Firewall settings
  - DNS resolution (`nslookup example.com`)
- For connection issues:
  - Check interface status with `ip link show`
  - Verify routing with `ip route`