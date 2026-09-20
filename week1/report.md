# Week 1 — Cyber Threat Intelligence Fundamentals

**Topic:** Meduza Stealer — CTI Fundamentals
**Author(s):** Meiram, Alikhan, Ulan

## 1. Glossary of Key CTI Terms

| Term | Definition |
|---|---|
| IOC (Indicator of Compromise) | A piece of forensic evidence — such as a file hash, IP address, domain name, or registry key — that indicates a system may have been compromised by a specific threat. |
| TTP (Tactics, Techniques, Procedures) | The behavior patterns of a threat actor: *tactics* are the "why" (goal), *techniques* are the "how" (method), and *procedures* are the specific implementation used by a particular actor or malware family. |
| Infostealer | A type of malware designed to silently collect sensitive data from an infected device — such as saved passwords, browser cookies, autofill data, and cryptocurrency wallet files — and send it back to the attacker. |
| C2 (Command and Control) | The server or infrastructure an attacker uses to communicate with infected machines — to send commands and receive stolen data. |
| CTI (Cyber Threat Intelligence) | Evidence-based knowledge about existing or emerging threats (actors, malware, infrastructure) used to inform security decisions and defense. |
| Dropper / Loader | A small, often lightly-obfuscated program whose only job is to download and execute the "real" malicious payload on the victim's machine, helping the main malware evade initial detection. |
| MaaS (Malware-as-a-Service) | A criminal business model where malware developers sell or rent access to their malware (with a control panel and support) to other criminals, who then run their own distribution campaigns. |

## 2. Classification of Threats and Their Sources

Classification of Meduza Stealer as a threat:

- **Threat type:** Financially-motivated infostealer (credential, browser-session, and crypto-wallet theft)
- **Source:** A cybercriminal group/developer offering Meduza Stealer as Malware-as-a-Service (MaaS), advertised and sold on underground Telegram channels and forums
- **Motivation:** Financial gain — stolen credentials, banking/crypto wallet data, and session tokens are either sold on dark web marketplaces or used directly by buyers of the MaaS subscription
- **Typical distribution channels:** Fake game cheats and trainers, cracked/pirated software, modded game files (e.g. Minecraft mods, CS2 cheats, Roblox scripts), often shared through Discord servers, YouTube "download" videos, and cheat-forum posts
- **Typical targets:** Gamers and general users searching for free cheats or cracked software — a group that is more likely to disable antivirus protection to run an "undetected" cheat executable, making them easier targets

## 3. What is Meduza Stealer?

Meduza Stealer is an infostealer malware family first observed being actively sold on
underground forums, distributed under the Malware-as-a-Service (MaaS) model — meaning its
developer sells access/subscriptions to other criminals rather than deploying it directly.
Buyers then run their own distribution campaigns, one of the most common being disguising
the malware as a "cheat," "trainer," or "mod" for popular games.

Once executed, Meduza Stealer collects a wide range of data from the victim's machine:
saved browser passwords and autofill data, session cookies (which can allow account
takeover even without a password), data from installed cryptocurrency wallet browser
extensions, and information from messaging applications such as Discord and Telegram. The
stolen data is packaged and sent back to the attacker's C2 infrastructure.

The "game cheat" distribution vector is particularly effective because it targets a very
large, often younger, audience that actively searches for and downloads unofficial
executables, and that community culture around cheats normalizes disabling antivirus or
ignoring security warnings to get a "cheat" to run — removing one of the main barriers that
would otherwise stop the infection.

## 4. Sources

- Vendor technical write-ups on Meduza Stealer (Uptycs, Cyfirma, Malwarebytes)
- VirusTotal community notes on submitted Meduza Stealer samples
- MITRE ATT&CK glossary of tactics/techniques terminology

## 5. Screenshots

See `screenshots/` folder for supporting evidence.
