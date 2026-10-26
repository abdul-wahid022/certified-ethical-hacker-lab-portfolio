<p align="center">
  <img src="./images/cover.png" alt="CEH module cover" width="800"/>
</p>

# Module 02: Footprinting and Reconnaissance

### Cloud Reconnaissance in four phases against a public domain

[Back to portfolio](../README.md)

---

## Overview

A four-phase reconnaissance exercise against `microsoft.com`, moving from passive domain intelligence to infrastructure discovery, attack surface analysis and social footprinting. The work ran from April 16 to April 28, 2026 as the IDS-CRACK Cloud Reconnaissance Framework.

|                  |                                                                                              |
| ---------------- | -------------------------------------------------------------------------------------------- |
| **Target**       | `microsoft.com` (public assets only)                                                         |
| **Approach**     | Passive and low-intensity: public data sources, DNS resolution, HTTP probing, username lookups |
| **Output**       | Findings are summarised here without hostnames or raw tool output                            |

## Phases

| Phase | Date             | Focus                                         | Tools                                                                  |
| ----- | ---------------- | --------------------------------------------- | ---------------------------------------------------------------------- |
| 1     | Apr 16 to 17     | Domain intelligence (passive OSINT)           | Google Dorking, Netcraft, DNSDumpster, theHarvester, Whois, Reverse Whois, Archive.org |
| 2     | Apr 17           | Infrastructure discovery                      | Subfinder, DNSrecon, nslookup, httpx, Shodan, Censys, Traceroute       |
| 3     | Apr 18           | Subdomain takeover detection, DNS resolution  | Subzy, DNSX, httpx, Amass, Recon-ng                                    |
| 4     | Apr 23 to 28     | Social footprint and AI-assisted OSINT        | Sherlock v0.15.0, SGPT (Shell GPT), theHarvester 4.10.1                |

## Findings

| Phase | Key results                                                                                                                                                           |
| ----- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| 1     | 76,856+ domains registered to the organisation, defensive registrations confirmed, 289+ subdomains from theHarvester, admin portals publicly indexed, public XLS and CSV sample files, strict SPF (`-all`), old Silverlight and ASPX endpoints visible in Archive.org |
| 2     | 49,273 subdomains from Subfinder, 652 confirmed live HTTP/HTTPS hosts, zone transfers blocked on all nameservers, strict DMARC (`p=reject`), Azure and Akamai multi-layer architecture |
| 3     | 6 subdomains confirmed vulnerable to takeover (dangling CNAMEs), CNAME chains of up to 4 hops, mixed HTTP and HTTPS hosts, 50 unique host endpoints enumerated        |
| 4     | Username `microsoft` found on 214+ platforms, strong presence on GitHub, npm, Docker Hub and Hugging Face, AI-driven theHarvester found 7 live hosts from the Baidu index |

## Recommendations From the Phase 3 Report

| Priority | Action                                                              |
| -------- | ------------------------------------------------------------------- |
| 1        | Remediate the confirmed subdomain takeover issues                   |
| 2        | Audit every CNAME record across all subdomains                      |
| 3        | Enforce HTTPS-only                                                  |
| 4        | Monitor subdomains continuously                                     |
| 5        | Review Azure Front Door and Traffic Manager configurations          |

## Notes

Subdomain takeover means an attacker claims a dangling CNAME target and serves content under a trusted subdomain. Only the count of affected subdomains is recorded here.
