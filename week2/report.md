# Week 2 — Data Collection Process

**Topic:** Meduza Stealer — OSINT Data Collection
**Author(s):** Meiram, Alikhan, Ulan

## 1. Open Source vs Closed Source Data

- **Open source data** — publicly available threat intelligence anyone can access without
  a paid subscription: public IOC feeds (ThreatFox, MalwareBazaar), researcher blog write-ups,
  public GitHub repositories, vendor blog posts.
- **Closed source data** — intelligence gated behind commercial platforms or private access
  (e.g. Silent Push Enterprise feeds, paid SOCRadar/ThreatFox Enterprise tiers), or internal
  telemetry only available to the vendor that collected it.

For this project we relied entirely on **open source** data, since it's freely reproducible
and verifiable by anyone reading this report.

## 2. OSINT Data Collection

### Public IOC Feed — ThreatFox (abuse.ch)
ThreatFox tracks Meduza Stealer under the malware family tag `win.meduza`. As of our
research date, the database entry shows:
- **First seen:** 2023-11-03
- **Last seen:** (ongoing — actively tracked)
- **Number of IOCs recorded:** 800+ (domains, IPs, URLs associated with Meduza C2 panels)
- Source: https://threatfox.abuse.ch/browse/malware/win.meduza/
- Cross-referenced with Malpedia entry: https://malpedia.caad.fkie.fraunhofer.de/details/win.meduza

### Public Researcher Repository
Found an open-source threat intel repository specifically dedicated to Meduza Stealer
research, maintained by an independent researcher, containing blocklists (plaintext + JSON)
and known malware sample hashes:
- Repository: https://github.com/Th3Tr1ckst3r/MeduzaResearch
- Notes: the researcher reports that in one takedown effort, 75+ servers used for
  distribution or as C2 panels for Meduza Stealer were taken offline, though operators kept
  a small number of C2s persistent afterward.

### VirusTotal
- Cross-checked a publicly shared VirusTotal Graph referenced by the researcher above,
  showing relationships between Meduza Stealer samples and related infrastructure:
  https://www.virustotal.com/graph/ga915589747524a0ca06b0003a4e6db69de78bcbae26a492d90dde9256f3dc6d0
- General approach for future/live hunting: submit suspicious "cheat" executables
  (collected from cheat forums/Discord — **only in an isolated sandbox, never run locally**)
  to VirusTotal and check detection ratio + community comments for Meduza Stealer tags.

### Background Research (attribution/origin)
- A widely-cited technical analysis links Meduza Stealer to a possible re-emergence of the
  older "Aurora Stealer" malware family: https://russianpanda.com/2023/06/28/Meduza-Stealer-or-The-Return-of-The-Infamous-Aurora-Stealer/
- Additional vendor coverage: NCC Group technical breakdown —
  https://research.nccgroup.com/2023/11/13/dont-throw-a-hissy-fit-defend-against-medusa/

### Maltego
- Not used this week — planned for a follow-up pass once a specific C2 domain/IP set is
  finalized, to visually map relationships between domains, hosting ASN, and sample hashes.

## 3. Data Source Mapping

| Source | Data type | What it provides |
|---|---|---|
| ThreatFox (abuse.ch) | Domains / IPs / URLs | Historical + tracked C2 panel indicators for `win.meduza` |
| MeduzaResearch GitHub repo | Hashes, blocklists | Community-curated IOC lists, sample hashes, screenshots |
| VirusTotal | File/URL reputation | Detection ratios, sample relationship graphs |
| Vendor blogs (russianpanda.com, NCC Group) | Analysis / attribution | Technical background on malware origin and behavior |

## 4. Raw Findings

See `data/` folder — contains links and notes collected during this week's research
(no live malware samples stored; only references to public sources, per safety practice).

## 5. Sources

- ThreatFox: https://threatfox.abuse.ch/browse/malware/win.meduza/
- Malpedia: https://malpedia.caad.fkie.fraunhofer.de/details/win.meduza
- MeduzaResearch (GitHub): https://github.com/Th3Tr1ckst3r/MeduzaResearch
- russianpanda.com technical analysis
- NCC Group Research blog

## 6. Screenshots

See `screenshots/` folder.
