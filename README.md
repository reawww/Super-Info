# Super Info

**Author:** Bocaletto Luca

## Overview

The **Super Info** is a comprehensive, command-line utility designed for system administrators working on Ubuntu 24 and Debian-based distributions. Developed entirely in Bash, it provides essential functionality for security monitoring and system checks without relying on an external GUI library. Instead, the tool "draws" its text-based interfaces with ASCII borders and colorized output—if your terminal supports colors—to improve readability.

This tool helps you quickly obtain critical system information and monitor various services. Its modular design includes the following features:

- **Info Sistema:** Displays basic system information such as OS name, kernel version, architecture, hostname, date/time, and locale.
- **Info Macchina:** Shows hardware specifications, including CPU details, memory usage, disk space, and network interfaces.
- **Info Utente:** Provides details about the current user (username, UID, groups, home directory, and recent login history).
- **Monitor Login e Servizi:** Runs a loop that refreshes every 5 seconds to display current login sessions and the status of critical services (e.g., sshd, apache2/nginx, mysqld/mariadb, postgresql). You can press **m** during the update wait time to exit this monitoring loop and return to the main menu.
- **Monitor Log Autenticazione:** Continuously shows the latest 20 events from `/var/log/auth.log` to help you track authentication-related incidents. Press **m** to break the loop and return to the menu.
- **Analisi Connettività e Porte Aperte:** Uses the `ss` command to scan and display all open ports on the system.
- **Controllo Integrità File di Sistema:** Runs an integrity check via `debsums`, comparing current file checksums with the expected ones from installed packages. It explains the process and displays any discrepancies (or a "system is integral" message if no errors are found).
- **Dashboard Avanzata:** Launches the real-time dashboard provided by Glances (if installed) for advanced system monitoring. Exit Glances by pressing **q** or **Ctrl+C** to return to the menu.
- **Audit e Correlazione Log:** Searches through the authentication logs for suspicious keywords (such as "failed," "invalid," or "error") and displays the last 30 matching entries.
- **Controllo Processi Sospetti:** Inspects the top 30 CPU-consuming processes and flags any processes that are not part of a predefined whitelist.
- **Esci:** Terminates the utility.

## Features

- **Clear, Text-Driven Interface:**  
  Each area of the tool is rendered in a visually organized manner using ASCII borders and centered titles. Color codes are applied (using `tput setaf` for universal compatibility) when your terminal supports at least 8 colors.

- **Universal Compatibility:**  
  The tool uses only standard commands available on Ubuntu and all Debian-based systems, ensuring it runs across all these environments.

- **Modular Design:**  
  Each function (system info, hardware info, etc.) is self-contained, making the tool easy to maintain and extend.

- **Real-Time Monitoring:**  
  Certain functions (monitoring login sessions and authentication logs) use loops that update every 5 seconds and allow you to break out by pressing **m** for "menu."

- **Automatic Dependency Checking:**  
  At startup, the tool checks for the presence of key packages (Glances and Debsums) and will prompt you to install missing dependencies automatically via `apt-get` if needed.

## Installation

1. **Requirements:**  
   - Ubuntu or another Debian-based system  
   - Bash shell  
   - `sudo` privileges (to install missing dependencies)

2. **Clone the Repository:**

   ```bash
   git clone https://github.com/bocaletto-luca/super-info.git
   cd super-info
