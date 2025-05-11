# 📂 Linux `mkdir` Command Cheat Sheet
## ℹ️ Introduction
The `mkdir` (make directory) command is used to create directories in Linux. This cheat sheet provides comprehensive guidance for both beginners and experienced users.

## 🚀 Basic Usage
```bash
mkdir dirname       # Create a single directory
mkdir dir1 dir2     # Create multiple directories
mkdir /path/to/dir  # Create directory at absolute path

# Practical examples:
mkdir ~/Projects    # Create Projects folder in home
mkdir /tmp/mydir    # Create directory in /tmp (requires permissions)
mkdir ./config      # Create config subdirectory
```

---

## 🔍 Common Options

| Option | Description | Example | Common Use Case |
|--------|-------------|---------|-----------------|
| `-p` | Create parent directories as needed | `mkdir -p a/b/c` | Nested directory creation |
| `-m` | Set permissions while creating | `mkdir -m 755 secure_dir` | Secure directory setup |
| `-v` | Verbose output | `mkdir -v newdir` | Confirmation of creation |

---

## 💡 Pro Tips
### Advanced Usage
```bash
# Create multiple nested directories
mkdir -p project/{src,test,docs}

# Create directory with specific permissions
mkdir -m 700 private_dir

# Create directory structure for web project
mkdir -p website/{public/{css,js,img},private/{config,logs}}
```

### Error Handling
- `mkdir: cannot create directory 'dirname': File exists` - Directory already exists
- `mkdir: cannot create directory 'dirname': Permission denied` - Need appropriate permissions

---

## 🏆 Best Practices
1. Always use `-p` when creating nested directories
2. Set appropriate permissions with `-m` for sensitive directories
3. Use verbose mode (`-v`) in scripts for better logging
4. Combine with `&&` to create and immediately enter directory:
   ```bash
   mkdir new_project && cd $_
   ```