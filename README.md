ar0x mirror

one command · the whole site · yours forever

bashdepends on wgetbeyond thatruns oncrafted by

divider

◆ the idea
wget ships preinstalled on virtually every Linux distro — so why install a downloader? ar0x mirror wraps the one honest command that archives an entire website into a tiny terminal app with a proper interface: guided input, live progress, and verification you can trust.

wget -mkEpnp -P ~/Downloads https://example.com
Everything else — the menus, the spinner, the report — is just ceremony around that line.

ar0x mirror in action

◆ quick start
curl -fsSL https://raw.githubusercontent.com/ar0x1/ar0xmirror/main/ar0xmirror -o ar0xmirrorchmod +x ar0xmirror./ar0xmirror
Cloned the repo instead? The script is already here — skip the curl.

Make it a command that works from anywhere:

mkdir -p ~/.local/binmv ar0xmirror ~/.local/bin/hash -rar0xmirror
◆ what the command does
flag	long form	what it buys you
-m	--mirror	recursive, infinite depth, timestamping — the whole tree
-k	--convert-links	rewrites links so pages point at your local files
-E	--adjust-extension	appends .html / .css where the server only implied a type
-p	--page-requisites	images, styles, scripts, fonts — everything a page needs
-np	--no-parent	never climbs above the start directory
-P	--directory-prefix	drops the mirror into ~/Downloads/<domain>/
Because it's --mirror, running it again later only fetches what changed.

◆ the experience
guided prompt	locked https:// prefix — paste a full URL, the protocol is stripped
single-key tuning	d folder · w wait · l limit · u agent · x flags · r reset
live progress	spinner · file count · bytes · speed · marching bar · last file saved
verification	runs du -sh and find | wc -l, shows the real output
history	remembers your last site — press enter to re-mirror it
safe exit	ctrl+c stops clean and keeps the partial mirror
◆ cli
ar0xmirror                  interactive (recommended)ar0xmirror example.com      start with a site prefilledar0xmirror example.com -y   mirror immediately, no menusar0xmirror -h | -v          help · version
◆ requirements
bash 4+ · wget · a terminal. Falls back to pure ASCII on non-UTF-8 terminals and respects NO_COLOR. No root, no packages, no accounts.

divider

◆ credits
crafted with wget, patience, and one long night by ar0x

mail · killtoneizuku@gmail.com · code · github.com/ar0x1

the web, now yours.
