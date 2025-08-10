### MultiTail Themes
MultiTail Themes is a set of dark, 256-color MultiTail color schemes (Tokyo Night, Dracula, Gruvbox) with opinionated regex highlights for real-world logs: severities, HTTP, SSH/Auth, DB/app messages, IPs, emails, timestamps, and a final catch-all.

## Features
Three dark themes: Tokyo Night, Dracula, Gruvbox (256-color friendly).

Log-aware highlights: ERROR/WARN/INFO/TRACE/DEBUG, HTTP methods & status codes, TLS, SSH auth, PAM, sessions, DB issues, PHP-FPM, upstream errors.

Extras: IPs, numbers, emails, timestamps, thread tags.

Catch-all rule: ensures unmatched text remains readable.

Simple install: drop into ~/.multitailrc (user) or /etc/multitail.conf (system).

## Requirements
A terminal with 256-color support (e.g., $TERM = xterm-256color).

multitail installed on your system (Linux/*BSD/macOS via pkg manager).

Installation
1. Clone the repository:
```
git clone https://github.com/yodabytz/multitail-themes.git
cd multitail-themes
```
2. Install for current user (recommended):
```
cat tokyonight.conf >> ~/.multitailrc
cat dracula.conf    >> ~/.multitailrc
cat gruvbox.conf    >> ~/.multitailrc
```
Or install system-wide (root):
```
cat tokyonight.conf >> /etc/multitail.conf
cat dracula.conf    >> /etc/multitail.conf
cat gruvbox.conf    >> /etc/multitail.conf
```
Usage
Automatic mapping (uses scheme:<name>:/var/log/ lines inside each theme):
```
multitail /var/log/syslog /var/log/auth.log
```
Force a theme per window:
```
# Tokyo Night
multitail -cS tokyonight /var/log/syslog -cS tokyonight /var/log/auth.log

# Dracula
multitail -cS dracula /var/log/syslog -cS dracula /var/log/auth.log

# Gruvbox
multitail -cS gruvbox /var/log/syslog -cS gruvbox /var/log/auth.log
```
Multiple files + follow (example):
```
multitail -cS tokyonight /var/log/nginx/access.log -cS tokyonight /var/log/nginx/error.log
```
## Configuration
All color indices are xterm-256 ANSI numbers chosen to be readable on a dark background.

Order matters. MultiTail applies rules top-to-bottom; the last matching rule wins.

Keep the catch-all as the last rule in each theme.

To adjust a color, change the leading number on a cs_re/cs_re_s line. Example:
```
# make WARN more orange (Tokyo Night)
cs_re:215,,bold:WARN
```
## Files
tokyonight.conf — Tokyo Night dark theme.
dracula.conf — Dracula dark theme.
gruvbox.conf — Gruvbox dark theme.
README.md

## Uninstallation
If you appended to an rc file, restore from your backup or remove the theme blocks manually from:

~/.multitailrc (user)

/etc/multitail.conf (system)

## Contributing
Open an issue or pull request with:

New log patterns (with sample lines).

Palette tweaks (state the ANSI index and reasoning).

Additional dark themes using the same structure.

## License
MIT License.

## Disclaimer
These themes and patterns are provided “as is.” Verify highlights and adjust rules to fit your environment and compliance requirements.
