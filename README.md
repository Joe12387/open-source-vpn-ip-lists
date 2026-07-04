# Open Source VPN IP Lists

Server / egress IP lists for major commercial VPN services — **one plain-text file per service**, one IP per line.

Every list is built from **first-party data** published by the VPN provider itself — not from third-party scraping, flow analysis, or GeoIP guesswork. If an IP is in a list, the provider itself said "this is one of our servers."

**Last updated:** 2026-07-04 · **Total IPs:** 17,190

## Lists

| File | Service | IPv4 | IPv6 |
|---|---|---:|---:|
| [airvpn.txt](airvpn.txt) | AirVPN | 1,020 | 1,020 |
| [ivpn.txt](ivpn.txt) | IVPN | 264 | — |
| [mullvad.txt](mullvad.txt) | Mullvad | 567 | 557 |
| [nordvpn.txt](nordvpn.txt) | NordVPN | 9,457 | — |
| [ovpn.txt](ovpn.txt) | OVPN.com | 96 | — |
| [pia.txt](pia.txt) | Private Internet Access | 1,463 | — |
| [protonvpn.txt](protonvpn.txt) | ProtonVPN | 1,437 | — |
| [riseupvpn.txt](riseupvpn.txt) | RiseupVPN | 20 | — |
| [surfshark.txt](surfshark.txt) | Surfshark | 281 | — |
| [windscribe.txt](windscribe.txt) | Windscribe | 1,008 | — |

## Format

- One IP address per line, nothing else — no comments, no CIDR suffixes (every entry is a single host).
- Sorted numerically, IPv4 first, then IPv6.
- Deduplicated within each file. The same IP may legitimately appear in two files (providers occasionally share infrastructure).

```
$ head -3 mullvad.txt
23.159.216.3
23.159.216.127
23.160.24.3
```

## Notes & caveats

- **These are the providers' server IPs** (entry/egress nodes). For full-tunnel consumer VPNs the entry IP is generally also the egress you'll see traffic from, but a few providers use split entry/exit pools — treat a match as "traffic associated with this VPN service," not proof of a specific exit.
- **IPv6 coverage varies** because the providers publish it unevenly: AirVPN and Mullvad publish v6 addresses; most others publish only v4.
- **Lists are snapshots.** VPN fleets churn constantly (NordVPN especially); an IP absent from the list may still be a VPN, and recently retired IPs may linger. Check the *Last updated* date above.
- Deliberately **excluded**: privacy relays (iCloud Private Relay), Tor exit nodes, and proxy networks — this repo is VPN services only.

## Use cases

Fraud/abuse triage, traffic classification, security research, or simply answering "is this IP a VPN?" without paying for a commercial VPN-detection API.

## License

Public domain under [CC0 1.0](LICENSE). IP lists are facts; do whatever you want with them. Attribution appreciated but not required.
