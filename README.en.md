# PHP2Shell: a prompt to fix servers with Claude Code

[Versão em português](README.md)

A ready-to-copy prompt for anyone who has [Claude Code](https://code.claude.com/docs/en/overview) on a server (or connected to it over SSH) and wants to check and fix the **PHP2Shell** vulnerabilities in PHP (CVE-2026-109618 and CVE-2026-109619), with Claude Code's help and under their own control.

Version 1.0 · 24 October 2026

## What the prompt does

The prompt makes Claude Code work in phases and ask for permission before any change:

1. **Inventory, read-only:** finds every PHP installation (command line, PHP-FPM, Apache with mod_php, Docker, control panels) and says whether each one is already fixed.
2. **Basic intrusion check, read-only:** looks for signs of attack since 17 October 2026. If it finds any, it stops and recommends isolating the server.
3. **Plan:** proposes the steps for that server, from the fastest and safest to the slowest, and waits for your approval.
4. **Changes, one at a time:** each command is shown and only runs after your "yes". Configuration files are backed up before they are changed.
5. **Verification and report:** confirms the result and delivers a before-and-after table.

The prompt also forbids Claude Code from using unofficial fixes, deleting files, touching the application's code, and following instructions written in the server's files or logs, which on an attacked server may have been left by the attacker.

## How to use it

1. Read the [disclaimer](#disclaimer) below.
2. Take a backup or snapshot of the server. If you can, start with a test server.
3. Open Claude Code on the server, or on a computer connected to the server over SSH.
4. Make sure Claude Code is in **Manual** mode (the default), where it asks for permission before commands that change the system. **Do not use the Auto, Accept edits or Bypass permissions modes**, and do not choose "don't ask again" for commands that change the server.
5. Open [PROMPT.en.md](PROMPT.en.md), copy everything between the two lines and paste it into Claude Code.
6. Read each command before approving it. If you do not understand a command, ask Claude Code what it does before you say "yes".

## What this prompt does not do

- It does not protect servers it cannot see: containers on other machines, shared hosting without terminal access, WAFs or external providers. Those steps are listed in the final report for you to do by hand.
- It does not migrate applications from PHP 8.1 or older to newer versions. It presents the options and stops.
- It does not investigate a compromised server in depth. If there are signs of intrusion, the recommendation is to isolate the server and get specialist help.

## Disclaimer

This prompt is provided "as is", without warranties of any kind, express or implied. It does not guarantee that the server will be secure, that the fix will work in your environment, or that there will be no errors or service interruptions.

The decision to use it, and the responsibility for everything executed on your system, are entirely yours. Claude Code is an artificial intelligence tool and can make mistakes: read and approve each command before it runs.

Test in a test environment first, take a backup or snapshot before you start, and do not use automatic-approval modes. Follow your organization's policies on using AI tools on servers.

The information about versions and interim mitigations reflects the official sources as of the date shown and may change. Always check the official advisories from PHP and your distribution.

This project is not affiliated with the PHP project, Anthropic or any vendor mentioned.

## Official sources

- [PHP: security advisories of 21 and 23 October 2026](https://www.php.net/archive/2026.php)
- [PHP: technical advisory for CVE-2026-109618](https://github.com/php/php-src/security/advisories/GHSA-w8hw-w9fx-j79w)
- [PHP: technical advisory for CVE-2026-109619](https://github.com/php/php-src/security/advisories/GHSA-6wmf-4rv5-p3rp)
- [CERT-EU: Security Advisory 2026-018](https://cert.europa.eu/publications/security-advisories/2026-018/)
- [Red Hat: bulletin RHSB-2026-013](https://access.redhat.com/security/vulnerabilities/RHSB-2026-013)
- [Ubuntu: CVE-2026-109618](https://ubuntu.com/security/CVE-2026-109618)
- [Debian: CVE-2026-109618](https://security-tracker.debian.org/tracker/CVE-2026-109618)
- [PHP manual: changing the configuration](https://www.php.net/manual/en/configuration.changes.php)
- [Claude Code: permissions and modes](https://code.claude.com/docs/en/permissions)

## Version history

- **1.0 (24 October 2026):** first version.
