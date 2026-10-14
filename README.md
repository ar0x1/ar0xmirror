<div align="center">

# ◈ ar0x mirror

### One command. The whole site. Yours to explore offline.

A terminal-first website mirroring tool built around **GNU Wget** — with guided setup, live progress, and a post-download report.

[![Shell: Bash](https://img.shields.io/badge/shell-Bash-222222?style=flat-square&logo=gnubash&logoColor=white)](https://www.gnu.org/software/bash/)
[![Powered by Wget](https://img.shields.io/badge/powered%20by-Wget-222222?style=flat-square)](https://www.gnu.org/software/wget/)
[![Platform: Linux](https://img.shields.io/badge/platform-Linux-222222?style=flat-square&logo=linux&logoColor=white)](https://www.kernel.org/)
[![License](https://img.shields.io/badge/license-check%20repository-555555?style=flat-square)](https://github.com/ar0x1/ar0xmirror)

<br/>

**Mirror a website locally without memorising a long Wget command.**

[Quick start](#-quick-start) · [Features](#-features) · [Usage](#-usage) · [How it works](#-how-it-works)

</div>

---

## ◈ What is ar0x mirror?

`ar0xmirror` is a Bash terminal interface for mirroring websites with Wget. It wraps Wget's mirroring options in a guided workflow, so you can enter a site, adjust crawl settings, watch progress, and review the resulting files.

Under the hood, its core command is:

```bash
wget -mkEpnp -P ~/Downloads https://example.com
```

The interface helps configure the crawl; **Wget performs the actual downloading**. Results depend on the target website, its access rules, and the resources Wget can reach.

## ✦ Features

| Feature | What it does |
| --- | --- |
| Guided workflow | Enter a website and review the crawl settings before starting. |
| Live progress | Displays progress information such as file count, downloaded size, elapsed time, transfer rate, and the latest saved path. |
| Crawl settings | Adjust the destination folder, request wait, rate limit, user agent, and extra Wget flags. |
| Command-line launch | Open the interactive interface or start with a prefilled site. |
| Automatic mode | Use `-y` / `--yes` to run with the tool's default settings without the interactive menus. |
| Completion report | Reports the resulting download size and file count. |
| Previous-site convenience | Remembers the last site for a quicker repeat run, where supported by the local environment. |
| Clean interruption | `Ctrl+C` stops the active run and keeps the partial mirror. |
| Terminal compatibility | Includes an ASCII fallback for terminals that cannot display the preferred characters and respects `NO_COLOR`. |

## ⚡ Quick start

### Requirements

- Linux or another compatible Unix-like environment
- Bash 4 or newer
- GNU Wget
- A terminal

The script checks for Wget when it starts. No language package manager or third-party Bash package is required by the documented script.

### Option A — Download the script

Run these commands in your terminal:

```bash
curl -fsSL https://raw.githubusercontent.com/ar0x1/ar0xmirror/main/ar0xmirror.txt -o ar0xmirror
chmod +x ar0xmirror
./ar0xmirror
```

If `curl` is unavailable, use `wget` to download the script:

```bash
wget -O ar0xmirror https://raw.githubusercontent.com/ar0x1/ar0xmirror/main/ar0xmirror.txt
chmod +x ar0xmirror
./ar0xmirror
```

### Option B — Clone the repository

```bash
git clone https://github.com/ar0x1/ar0xmirror.git
cd ar0xmirror
```

The repository currently stores the script source as `ar0xmirror.txt`. Make an executable copy:

```bash
cp ar0xmirror.txt ar0xmirror
chmod +x ar0xmirror
./ar0xmirror
```
