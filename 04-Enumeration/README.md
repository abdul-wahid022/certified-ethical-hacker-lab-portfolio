<div align="center">

<img src="./images/cover.png" alt="CEH Module 04 — Enumeration" width="100%" />

<br><br>

<h1>Module 04 — Enumeration</h1>
<h3>Advanced Reconnaissance and Attack Surface Mapping Across Legacy and Hardened Systems</h3>

<br>

<img src="https://img.shields.io/badge/MODULE-04%20%2F%2020-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/STATUS-COMPLETED-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/TECHNIQUES-6-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/ENVIRONMENT-ISOLATED%20LAB-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />

<br><br>

<a href="#lab-topology"><b>Topology</b></a> &nbsp;·&nbsp;
<a href="#techniques"><b>Techniques</b></a> &nbsp;·&nbsp;
<a href="#key-contrast"><b>Contrast</b></a> &nbsp;·&nbsp;
<a href="#key-takeaways"><b>Takeaways</b></a> &nbsp;·&nbsp;
<a href="#full-report"><b>Full Report</b></a>

</div>

<br>

---

## Executive Summary

This module documents a deep enumeration phase covering six techniques against intentionally vulnerable systems and modern hardened Windows systems. The contrast between the two shows how much legacy configuration exposes and what a hardened system still leaves visible.

Tools used were **enum4linux, CrackMapExec, AD Explorer, kerbrute, Gobuster, ffuf and Nikto**.

> All testing was performed in a private virtual network. All credentials and IP addresses shown are lab-only values.

<br>

## Lab Topology

<table>
<tr><th>Item</th><th>Detail</th></tr>
<tr><td><b>Network</b></td><td>VirtualBox host-only network <code>192.168.100.0/24</code></td></tr>
<tr><td><b>Legacy Targets</b></td><td>Metasploitable 2 · DVWA</td></tr>
<tr><td><b>Hardened Targets</b></td><td>Windows 10 · Windows Server 2025 (domain controller)</td></tr>
</table>

<br>

## Techniques

<table>
<tr><th>Technique</th><th>What Was Done</th></tr>
<tr><td><b>SMB/CIFS Enumeration</b></td><td>Null sessions, share, user and group extraction with <code>enum4linux</code> and <code>CrackMapExec</code></td></tr>
<tr><td><b>LDAP / Active Directory</b></td><td>Anonymous binds, <code>AD Explorer</code>, domain structure mapping</td></tr>
<tr><td><b>Kerberos User Enumeration</b></td><td><code>kerbrute</code> against port 88</td></tr>
<tr><td><b>RPC / DCOM Enumeration</b></td><td>Endpoint mapping, 351 to 527 endpoints including SAM and DRSUAPI</td></tr>
<tr><td><b>Web Service Enumeration</b></td><td>Fingerprinting, directory brute-forcing with <code>Gobuster</code> and <code>ffuf</code>, <code>Nikto</code>, API discovery</td></tr>
<tr><td><b>Database Enumeration</b></td><td>Unauthenticated MySQL access and offline hash cracking</td></tr>
</table>

<br>

## Key Contrast

<table>
<tr><th>System</th><th>Result</th></tr>
<tr><td><b>Metasploitable 2</b></td><td>Null SMB sessions, unauthenticated MySQL root access, exposed admin panels</td></tr>
<tr><td><b>Windows 10 and Server 2025</b></td><td>Null sessions correctly blocked, but RPC, LDAP and Kerberos still expose surfaces that support follow-up attacks such as Kerberoasting and AS-REP Roasting</td></tr>
</table>

<br>

## Key Takeaways

- **Legacy systems expose a lot.** Null sessions and unauthenticated database access gave direct visibility into users, shares and data.
- **Hardening helps but does not hide everything.** Blocked null sessions still left RPC, LDAP and Kerberos visible.
- **Enumeration feeds the next attack.** Exposed Kerberos and directory data support Kerberoasting and AS-REP Roasting.
- **Web services need their own enumeration.** Fingerprinting and directory brute-forcing found admin panels and APIs.

<br>

## Lab Environment

| | |
|---|---|
| **Network** | VirtualBox host-only network `192.168.100.0/24` |
| **Targets** | Metasploitable 2 · DVWA · Windows 10 · Windows Server 2025 (domain controller) |
| **Tools Used** | `enum4linux` `CrackMapExec` `AD Explorer` `kerbrute` `Gobuster` `ffuf` `Nikto` |
| **Scope** | Isolated lab only |

<br>

## Full Report

The complete report is available here:

📄 **[Enumeration.pdf](./Enumeration.pdf)**

<br>

## Disclaimer

This lab was conducted in a private, isolated virtual environment built solely for educational purposes under the EC-Council CEH curriculum. No real production systems or live targets were accessed.

<br>

<div align="center">

⬅ <a href="../"><b>Back to Main Repository</b></a>

</div>
