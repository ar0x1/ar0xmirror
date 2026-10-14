ar0x mirror
one command · the whole site · yours forever

bashdepends onbeyond thatruns oncrafted by


◆ the idea
wget ships preinstalled on virtually every Linux distro — so why install a downloader?ar0x mirror wraps the one honest command that archives an entire website into a tinyterminal app with a proper interface: guided input, live progress, and verification you can trust.

wget -mkEpnp -P ~/Downloads https://example.com
Everything else — the menus, the spinner, the report — is just ceremony around that line.

ar0x mirror in action
◆ quick start
curl -fsSL https://raw.githubusercontent.com/ar0x1/ar0xmirror/main/ar0xmirror -o ar0xmirrorchmod +x ar0xmirror./ar0xmirror
If you cloned the repo, skip the curl — the script is already here.

Make it a command you can launch from anywhere:

mkdir -p ~/.local/binmv ar0xmirror ~/.local/bin/hash -rar0xmirror              # now works from any folder
◆ what the command does
flag	long form	what it buys you
-m	--mirror	recursive, infinite depth, timestamping — the whole tree
-k	--convert-links	rewrites links so pages point at your local files
-E	--adjust-extension	appends .html / .css where the server only implied a type
-p	--page-requisites	images, styles, scripts, fonts — everything a page needs
-np	--no-parent	never climbs above the start directory
-P	--directory-prefix	drops the mirror into ~/Downloads/<domain>/
And because it's --mirror, running it again later only fetches what changed.

◆ the experience
guided prompt	locked https:// prefix — paste a full URL, the protocol is stripped for you
single-key tuning	d folder · w wait · l limit · u agent · x flags · r reset
live progress	spinner · file count · bytes on disk · transfer speed · marching bar · last file saved
verification	runs du -sh and find | wc -l and shows the real output
history	remembers your last site — press enter to re-mirror it
safe exit	ctrl+c stops clean and keeps the partial mirror
◆ cli
ar0xmirror                  interactive (recommended)ar0xmirror example.com      start with a site prefilledar0xmirror example.com -y   mirror immediately, no menusar0xmirror -h | -v          help · version
◆ requirements
bash 4+ · wget · a terminal. Falls back to pure ASCII on non-UTF-8 terminalsand respects NO_COLOR. Nothing else — no root, no packages, no accounts.

◆ credits
crafted with wget, patience, and one long night by ar0x

mail · killtoneizuku@gmail.com · code · github.com/ar0x1


the web, now yours.
