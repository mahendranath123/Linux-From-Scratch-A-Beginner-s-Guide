<div align="center">
  <img src="https://img.shields.io/badge/Linux-User%20Management-brightgreen" alt="User Management" />
  <img src="https://img.shields.io/badge/Security-Access%20Control-blue" alt="Access Control" />
  <img src="https://img.shields.io/badge/Multi-User-System-orange" alt="Multi-User" />
</div>

# 👥 Linux User Management Guide
A modern, detailed walkthrough for managing users and groups on Linux. Ensure secure, organized access control for both personal and enterprise environments.

---

## 📋 Table of Contents
1. [Introduction](#introduction)
2. [Key Configuration Files](#key-configuration-files)
3. [Creating Users](#creating-users)
4. [Managing Passwords](#managing-passwords)
5. [Modifying Users](#modifying-users)
6. [Deleting Users](#deleting-users)
7. [Group Management](#group-management)
8. [Sudo & Privilege Escalation](#sudo--privilege-escalation)
9. [Pro Tips & Best Practices](#pro-tips--best-practices)

---

## 📖 Introduction
Linux is a **multi-user** operating system designed to allow multiple individuals to access and operate on a system simultaneously. Effective user management is critical for:

- 🔒 **Security**: Restricting unauthorized access.
- 🛠️ **Control**: Defining roles and permissions.
- 🧹 **Integrity**: Maintaining clean audit trails and separation of duties.

---

## 🔑 Key Configuration Files
| File             | Purpose                                            |
|------------------|----------------------------------------------------|
| `/etc/passwd`    | User account details (username, UID, GID, shell).  |
| `/etc/shadow`    | Encrypted passwords and password policies.         |
| `/etc/group`     | Group definitions (group name, GID, members).      |
| `/etc/gshadow`   | Secure group passwords and admin/member lists.     |

> **🔒 Security Note:** Limit direct edits; use commands (`useradd`, `groupadd`) to avoid syntax errors.

---

## 👷 Creating Users

### 1. `useradd` (Universal)
```bash
# Basic user without home directory
sudo useradd username

# Create user with home directory
sudo useradd -m username

# Specify login shell
sudo useradd -m -s /bin/bash username
```

### 2. `adduser` (Debian/Ubuntu Interactive)
```bash
sudo adduser username
```
> **💡 Tip:** `adduser` prompts for full name, room, work phone—great for enterprise setups.

---

## 🔑 Managing Passwords

### Set or Change Password
```bash
sudo passwd username
```

### Enforce Password Policies
| Task                    | Command                                      |
|-------------------------|----------------------------------------------|
| Set max password age    | `sudo chage -M 90 username`                  |
| Set min password age    | `sudo chage -m 7 username`                   |
| Set warning period      | `sudo chage -W 7 username`                   |
| Lock account            | `sudo passwd -l username`                    |
| Unlock account          | `sudo passwd -u username`                    |

> **🛡️ Security Best Practice:** Expire default passwords immediately.

---

## 🛠 Modifying Users

| Change                   | Command                                                   |
|--------------------------|-----------------------------------------------------------|
| Username                 | `sudo usermod -l new_username old_username`               |
| Home directory           | `sudo usermod -d /new/home -m username`                  |
| Default shell            | `sudo usermod -s /bin/zsh username`                      |
| Primary group            | `sudo usermod -g newgroup username`                      |
| Add secondary groups     | `sudo usermod -aG group1,group2 username`                |

---

## 🗑 Deleting Users
```bash
# Remove user but keep home directory
dsudo userdel username

# Remove user and home directory
dsudo userdel -r username
```
> **⚠️ Warning:** Check permissions and backups before deletion.

---

## 👥 Group Management

### Create a Group
```bash
sudo groupadd groupname
```

### Add/Remove Users
```bash
# Add to group
sudo usermod -aG groupname username

# Remove from group (Debian)
sudo gpasswd -d username groupname
```

### View Group Memberships
```bash
groups username
```

---

## 🛡️ Sudo & Privilege Escalation

### Grant Sudo Access
| Distro Family  | Command                                                 |
|----------------|---------------------------------------------------------|
| Debian/Ubuntu  | `sudo usermod -aG sudo username`                        |
| RHEL/CentOS    | `sudo usermod -aG wheel username`                       |

### Fine-Grained Sudoers
```bash
sudo visudo
# Add line:
username ALL=(ALL) NOPASSWD: /usr/bin/systemctl restart apache2
```
> **📝 Note:** Use `visudo` to prevent syntax mistakes.

---

## 💡 Pro Tips & Best Practices
- **Use Consistent UID/GID Ranges** for automated deployments.
- **Implement `nscd` or `sssd`** for network-based account caching.
- **Restrict SSH** by disabling root login (`PermitRootLogin no` in `/etc/ssh/sshd_config`).
- **Audit Changes**: Monitor `/var/log/auth.log` or `/var/log/secure`.
- **Automate** with Ansible or Chef for large environments.

---



