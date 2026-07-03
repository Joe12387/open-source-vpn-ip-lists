# open-source-vpn-ip-lists

Server / egress IP lists for major commercial VPN services — **one plain-text file per service**, one IP per line.

Every list is built from **first-party data**: the VPN provider's own published server API (the same way AWS publishes its IP ranges) — not from third-party scraping, flow analysis, or GeoIP guesswork. If an IP is in a list, the provider itself said "this is one of our servers."

**Last updated:** 2026-07-03 · **Total IPs:** 16,956

## Lists

| File | Service | IPv4 | IPv6 | Source |
|---|---|---:|---:|---|
| [airvpn.txt](airvpn.txt) | AirVPN | 1,020 | 1,020 | [airvpn.org/api/status](https://airvpn.org/api/status/) |
| [ivpn.txt](ivpn.txt) | IVPN | 264 | — | [api.ivpn.net/v5/servers.json](https://api.ivpn.net/v5/servers.json) |
| [mullvad.txt](mullvad.txt) | Mullvad | 567 | 557 | [api.mullvad.net/www/relays/all](https://api.mullvad.net/www/relays/all/) |
| [nordvpn.txt](nordvpn.txt) | NordVPN | 9,482 | — | [api.nordvpn.com/v1/servers](https://api.nordvpn.com/v1/servers?limit=0) |
| [ovpn.txt](ovpn.txt) | OVPN.com | 96 | — | [ovpn.com/v2/api/client/entry](https://www.ovpn.com/v2/api/client/entry) |
| [pia.txt](pia.txt) | Private Internet Access | 1,202 | — | [serverlist.piaservers.net](https://serverlist.piaservers.net/vpninfo/servers/v6) |
| [protonvpn.txt](protonvpn.txt) | ProtonVPN | 1,437 | — | ProtonVPN client API (`/vpn/v1/logicals`, authenticated session) |
| [riseupvpn.txt](riseupvpn.txt) | RiseupVPN | 20 | — | [api.black.riseup.net eip-service](https://api.black.riseup.net/3/config/eip-service.json) |
| [surfshark.txt](surfshark.txt) | Surfshark | 280 | — | [api.surfshark.com/v4/server/clusters](https://api.surfshark.com/v4/server/clusters) (hostnames, DNS-resolved) |
| [windscribe.txt](windscribe.txt) | Windscribe | 1,011 | — | [assets.windscribe.com serverlist](https://assets.windscribe.com/serverlist/mob-v2/1/1) |

## Format

- One IP address per line, nothing else — no comments, no CIDR suffixes (every entry is a single host).
- Sorted numerically, IPv4 first, then IPv6.
- Deduplicated within each file. The same IP may legitimately appear in two files (providers occasionally share infrastructure).

```
$ head -3 mullvad.txt
31.171.153.66
31.171.154.50
37.19.196.65
```

## Notes & caveats

- **These are the providers' server IPs** (entry/egress nodes). For full-tunnel consumer VPNs the entry IP is generally also the egress you'll see traffic from, but a few providers use split entry/exit pools — treat a match as "traffic associated with this VPN service," not proof of a specific exit.
- **IPv6 coverage varies** because the providers publish it unevenly: AirVPN and Mullvad publish v6 addresses; most others list only v4 in their APIs.
- **Surfshark** publishes cluster hostnames rather than raw IPs, so its list is DNS-resolved from those hostnames at build time.
- **Lists are snapshots.** VPN fleets churn constantly (NordVPN especially); an IP absent from the list may still be a VPN, and recently retired IPs may linger. Check the *Last updated* date above.
- Deliberately **excluded**: privacy relays (iCloud Private Relay), Tor exit nodes, and proxy networks — this repo is VPN services only.

## Use cases

Fraud/abuse triage, traffic classification, security research, or simply answering "is this IP a VPN?" without paying for a commercial VPN-detection API.

## License

Public domain under [CC0 1.0](LICENSE). IP lists are facts; do whatever you want with them. Attribution appreciated but not required.
