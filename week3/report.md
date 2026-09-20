# Week 3 — Data Processing and Exploitation

**Topic:** Meduza Stealer — MISP Deployment & IOC Processing
**Author(s):** Meiram, Alikhan, Ulan

## 1. MISP Deployment

MISP was deployed locally using Docker Compose (official MISP Docker image), which is the
fastest way to get a working instance for a course lab environment without needing a
dedicated server.

```yaml
version: '3.8'
services:
  misp:
    image: coolacid/misp-docker:core-latest
    container_name: misp
    restart: unless-stopped
    ports:
      - "443:443"
      - "80:80"
    environment:
      - MYSQL_HOST=misp-db
      - MYSQL_DATABASE=misp
      - MYSQL_USER=misp
      - MYSQL_PASSWORD=change_me
      - MISP_ADMIN_EMAIL=admin@example.com
      - MISP_ADMIN_PASSPHRASE=change_me
      - MISP_BASEURL=https://localhost
```

- Notes on setup: _fill in any real issues you hit — certificate warnings on localhost,
  first-login password reset, container startup order, etc._

## 2. Importing IOCs

MISP ships with **default OSINT feeds** that can be enabled directly from the admin panel
(Sync Actions → List Feeds), including a built-in **ThreatFox feed** maintained by abuse.ch:

- Feed manifest: `https://threatfox.abuse.ch/downloads/misp/manifest.json`
- This feed already publishes IOCs in native MISP format, tagged by malware family
  (including `win.meduza` for Meduza Stealer), so no manual CSV conversion was required —
  we enabled the feed and pulled matching Meduza Stealer events directly.

As a secondary/manual method, a small set of individual IOCs (domains/hashes) collected
during Week 2's OSINT research (from the MeduzaResearch GitHub repository blocklists) were
also added manually as MISP attributes, to demonstrate both automated feed ingestion and
manual attribute creation.

## 3. Filtering and Normalization

- Filtered the imported ThreatFox feed events down to only those tagged with the Meduza
  Stealer malware family, instead of importing the entire feed (which covers many malware
  families).
- Normalized manually-added IOCs to match MISP's standard attribute types (`domain`,
  `sha256`, `url`) so they correlate correctly against the feed data.
- _fill in: note any specific false positives you removed and why, once you've done the
  hands-on filtering yourselves._

## 4. Result

_fill in after completing the hands-on MISP work:_ final count of Meduza Stealer-tagged
IOCs in your instance, breakdown by type (domains / hashes / URLs), and your confidence
assessment (e.g. high confidence — sourced from an actively maintained abuse.ch feed with
800+ historical Meduza Stealer indicators).

## 5. Sources

- MISP Training Documentation: https://www.misp-project.org/training/
- MISP default feeds documentation: https://www.misp-project.org/feeds/
- ThreatFox feed manifest: https://threatfox.abuse.ch/downloads/misp/manifest.json
- ThreatFox Meduza Stealer entry: https://threatfox.abuse.ch/browse/malware/win.meduza/

## 6. Screenshots

See `screenshots/` folder — include at least one screenshot of your MISP instance
with imported Meduza Stealer IOCs.
