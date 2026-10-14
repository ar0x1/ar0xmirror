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

### Optional — Make it available as a command

After downloading or copying the script:

```bash
mkdir -p ~/.local/bin
install -m 755 ar0xmirror ~/.local/bin/ar0xmirror
```

Make sure `~/.local/bin` is on your `PATH`. If it is not, add this line to your shell startup file (for Bash, commonly `~/.bashrc`):

```bash
export PATH="$HOME/.local/bin:$PATH"
```

Reload the configuration:

```bash
source ~/.bashrc
```

Then launch it from any directory:

```bash
ar0xmirror
```

## ⌘ Usage

### Interactive mode

Start the guided interface:

```bash
ar0xmirror
```

Enter a domain when prompted, then review the destination and crawl settings before starting the mirror.

### Start with a site prefilled

```bash
ar0xmirror example.com
```

You can also pass a full URL; the script normalises the site input before building the HTTPS URL.

### Run without the menus

```bash
ar0xmirror example.com --yes
```

Short form:

```bash
ar0xmirror example.com -y
```

This uses the tool's default settings without opening the interactive menus. Review the destination and site before using automatic mode.

### Help and version

```bash
ar0xmirror --help
ar0xmirror --version
```

Short forms:

```bash
ar0xmirror -h
ar0xmirror -v
```

## ⚙ Interactive settings

In the settings screen, the current script provides these keyboard shortcuts:

| Key | Action |
| --- | --- |
| `Enter` | Start the mirror with the current settings |
| `d` | Change the destination folder |
| `w` | Set the wait time between requests |
| `l` | Set a download rate limit, such as `500k` or `2m` |
| `u` | Set a custom user-agent string |
| `x` | Add extra Wget flags |
| `r` | Reset settings to their defaults |
| `b` | Go back to choose another site |
| `q` | Quit the settings screen |

The interface may show additional hints in context. Press `Ctrl+C` during a mirror to interrupt it; the partial download is retained.

## 🧰 How it works

The script builds a Wget command using these core options:

| Option | Meaning |
| --- | --- |
| `-m` | Mirror mode: recursive retrieval with timestamping and infinite recursion depth. |
| `-k` | Convert links so downloaded pages can link to local copies. |
| `-E` | Adjust extensions for files served with a content type that implies an extension. |
| `-p` | Download page requisites such as images and stylesheets. |
| `-np` | Do not ascend to the parent directory above the starting URL. |
| `-P` | Choose the local directory in which Wget stores downloaded content. |
| `-nv` | Use non-verbose output, which the interface can parse for progress details. |

The default destination is `~/Downloads`. The tool places the mirrored site under a directory based on its host name.

> **Note:** Website mirroring is not the same as cloning a live service. Dynamic applications, authenticated content, API-driven pages, and resources blocked by a server may not work offline. Always respect the website's terms, copyright, robots policy, and applicable law.

## 📁 Output and verification

After the crawl, the script uses local filesystem tools to report information about the downloaded output, including its total size and file count.

For a quick manual check, inspect the directory where you saved the mirror. For example, with the default destination:

```bash
ls -lah ~/Downloads
```

The precise folder name and completeness depend on the URL and the server's response.

## 🛠 Troubleshooting

**`wget: command not found`**

Install GNU Wget using your operating system's package manager, then run the script again.

Debian / Ubuntu:

```bash
sudo apt update
sudo apt install wget
```

Fedora:

```bash
sudo dnf install wget
```

Arch Linux:

```bash
sudo pacman -S wget
```

**`Permission denied`**

Make the script executable:

```bash
chmod +x ar0xmirror
```

**`ar0xmirror: command not found`**

Run it from the current directory with `./ar0xmirror`, or confirm that `~/.local/bin` is on your `PATH`.

**The downloaded website is incomplete**

Some sites rely on JavaScript, login sessions, APIs, anti-bot protections, or resources on other domains. Wget cannot guarantee a fully functional offline copy of every website.

**The terminal characters look wrong**

Use a UTF-8-capable terminal or let the script's ASCII fallback handle unsupported characters. The script also respects `NO_COLOR` in environments that request no coloured output.

## 🔐 Responsible use

Use ar0x mirror only on websites you are authorised to archive. Avoid overwhelming servers; configure a wait interval or rate limit when appropriate. Do not use mirroring to bypass access controls or copy private content without permission.

## 👤 Author

Created by **ar0x**.

- GitHub: [@ar0x1](https://github.com/ar0x1)
- Repository: [ar0x1/ar0xmirror](https://github.com/ar0x1/ar0xmirror)

---

<div align="center">

**The web, now yours.**

<sub>Built with Bash and GNU Wget.</sub>

</div>
