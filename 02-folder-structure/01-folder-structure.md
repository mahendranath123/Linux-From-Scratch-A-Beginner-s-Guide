<div align="center">
  <img src="https://img.shields.io/badge/Linux-Filesystem-ff69b4" alt="Filesystem" />
  <img src="https://img.shields.io/badge/Structure-Guide-blue" alt="Structure Guide" />
  <img src="https://img.shields.io/badge/Modern-Layout-green" alt="Modern Layout" />
</div>

# 🌳 Understanding the Linux Folder Structure
A modern, visual guide to Linux directories, their purposes, and how they interconnect. Perfect for new admins, container developers, and enthusiasts!

---

## 📋 Table of Contents
1. [Overview](#overview)
2. [Symbolic Links](#symbolic-links)
3. [Important System Directories](#important-system-directories)
4. [User & Application Directories](#user--application-directories)
5. [Temporary & Virtual Filesystems](#temporary--virtual-filesystems)
6. [Mount Points](#mount-points)
7. [Pro Tips](#pro-tips)

---

## 🔍 1. Overview
Linux organizes files in a **single hierarchical tree** starting from the root (`/`). Each directory (`/etc`, `/var`, etc.) has a well-defined role to keep the system clean, secure, and efficient.

---

## 🔗 2. Symbolic Links (Less Significant)
Symbolic links point to final locations, simplifying paths without duplicating data.

| Link            | Points To        | Purpose                                               |
|-----------------|------------------|-------------------------------------------------------|
| `/sbin` → `/usr/sbin`   | System admin binaries | Admin commands (low-level)                           |
| `/bin` → `/usr/bin`     | User binaries   | Essential tools available to all users                |
| `/lib` → `/usr/lib`     | Shared libraries| Core libraries and kernel modules                     |

> 🔗 **Note:** These are often legacy links; modern distros merge `/bin`, `/sbin`, and `/lib` into `/usr` for simplicity.

---

## 🛡️ 3. Important System Directories
| Directory | Description                                              |
|-----------|----------------------------------------------------------|
| `/boot`   | Kernel & bootloader files (not used in containers)       |
| `/usr`    | Secondary hierarchy for user-installed apps & libraries  |
| `/var`    | Variable data: logs, caches, mail, spool files          |
| `/etc`    | System-wide configuration files                          |

---

## 👥 4. User & Application Directories
| Directory | Description                                        |
|-----------|----------------------------------------------------|
| `/home`   | Default location for user home directories         |
| `/opt`    | Optional add-on software packages                  |
| `/srv`    | Service data (e.g., web, FTP)                     |
| `/root`   | Home directory for the root (superuser)           |

---

## 🛠️ 5. Temporary & Virtual Filesystems
| Directory   | Description                                                         |
|-------------|---------------------------------------------------------------------|
| `/tmp`      | Temporary files, cleared on reboot                                  |
| `/run`      | Runtime data for processes (volatile)                               |
| `/proc`     | Virtual FS: process & kernel info (`procfs`)                        |
| `/sys`      | Virtual FS: device & kernel interface (`sysfs`)                     |
| `/dev`      | Device nodes (e.g., `/dev/null`, `/dev/sda`)                        |

---

## 📂 6. Mount Points
| Directory | Description                                              |
|-----------|----------------------------------------------------------|
| `/mnt`    | Temporary mount point for external filesystems           |
| `/media`  | Removable media (USB, CD/DVD)                            |
| `/data`   | Custom mounts (e.g., Windows volume `C:/ubuntu-data`)    |

---

## 💡 Pro Tips
- **Container-Friendly**: In Docker, only mount what you need; ignore `/proc`, `/sys` as they’re auto-mounted.
- **Security**: Restrict write permissions on `/etc` and `/var` to prevent tampering.
- **Backups**: Focus on `/etc`, `/home`, and `/var`—most configs and data reside here.
- **Visualization**: Use `tree / --dirsfirst -L 2` to get a quick directory snapshot.

---

> _“A clear directory structure is the backbone of system reliability and maintainability.”_ 🚀

