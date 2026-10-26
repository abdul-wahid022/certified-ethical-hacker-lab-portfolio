<div align="center">

<img src="./images/cover.png" alt="CEH Module 03 — Scanning Networks" width="100%" />

<br><br>

<h1>Module 03 — Scanning Networks</h1>
<h3>Advanced Host Discovery and Port Analysis in an Isolated Lab</h3>

<br>

<img src="https://img.shields.io/badge/MODULE-03%20%2F%2020-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/STATUS-COMPLETED-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/ENVIRONMENT-ISOLATED%20LAB-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />
<img src="https://img.shields.io/badge/TOOLS-4-0d1117?style=for-the-badge&labelColor=0d1117&color=00b4d8" />

<br><br>

<a href="#lab-topology"><b>Topology</b></a> &nbsp;·&nbsp;
<a href="#coverage"><b>Coverage</b></a> &nbsp;·&nbsp;
<a href="#outcome"><b>Outcome</b></a> &nbsp;·&nbsp;
<a href="#key-takeaways"><b>Takeaways</b></a> &nbsp;·&nbsp;
<a href="#full-report"><b>Full Report</b></a>

</div>

<br>

---

## Executive Summary

This module documents a hands-on progression through the scanning phase of a security assessment, from foundational techniques to evasion and automation, using **hping3, Nmap, Zenmap and Metasploit**.

All scans ran inside an isolated lab with no internet access.

> All testing was performed in a private virtual network. All IP addresses shown are lab-only values.

<br>

## Lab Topology

<table>
<tr><th>Item</th><th>Detail</th></tr>
<tr><td><b>Network</b></td><td>VirtualBox host-only network <code>192.168.100.0/24</code></td></tr>
<tr><td><b>Target 1</b></td><td>Metasploitable 2</td></tr>
<tr><td><b>Target 2</b></td><td>Ubuntu with DVWA</td></tr>
<tr><td><b>Target 3</b></td><td>Windows 10</td></tr>
</table>

<br>

## Coverage

<table>
<tr><th>Area</th><th>Techniques</th></tr>
<tr><td><b>Host Discovery</b></td><td>Custom packet crafting with <code>hping3</code></td></tr>
<tr><td><b>Scan Types</b></td><td>TCP SYN, SYN-ACK, FIN, RST, NULL and Idle (Zombie) scanning</td></tr>
<tr><td><b>Firewall Behaviour</b></td><td>Detecting ICMP and TCP filtering</td></tr>
<tr><td><b>Port State Classification</b></td><td>SYN, Connect and ACK scans</td></tr>
<tr><td><b>Evasion</b></td><td>Fragmentation, source port manipulation, decoy scanning</td></tr>
<tr><td><b>Automation</b></td><td>Adaptive multi-target scanners</td></tr>
<tr><td><b>GUI Analysis</b></td><td><code>Zenmap</code></td></tr>
<tr><td><b>Framework Scanning</b></td><td>Metasploit auxiliary modules, compared against standalone Nmap results</td></tr>
</table>

<br>

## Outcome

Hosts were discovered reliably, port states were classified, firewall filtering behaviour was identified, and evasion techniques were applied. Results from standalone Nmap and Metasploit workflows were checked for consistency.

<br>

## Key Takeaways

- **Different scan types answer different questions.** SYN, ACK, FIN, NULL and Idle scans reveal different things about port state and filtering.
- **Firewalls leave fingerprints.** ICMP and TCP filtering behaviour can be identified from how a target responds.
- **Evasion changes what a scanner sees.** Fragmentation, source port manipulation and decoys alter scan traffic.
- **Cross-checking builds confidence.** Comparing Metasploit and Nmap results confirms that findings are consistent.

<br>

## Lab Environment

| | |
|---|---|
| **Network** | VirtualBox host-only network `192.168.100.0/24` |
| **Targets** | Metasploitable 2 · Ubuntu with DVWA · Windows 10 |
| **Tools Used** | `hping3` `Nmap` `Zenmap` `Metasploit` |
| **Scope** | Isolated lab, no internet access |

<br>

## Full Report

The complete report is available here:

📄 **[Scanning.pdf](./Scanning.pdf)**

<br>

## Disclaimer

This lab was conducted in a private, isolated virtual environment built solely for educational purposes under the EC-Council CEH curriculum. No real production systems or live targets were scanned.

<br>

<div align="center">

⬅ <a href="../"><b>Back to Main Repository</b></a>

</div>
