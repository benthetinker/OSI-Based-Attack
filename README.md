# OSI-Based-Attack

| Layer           | Example Attacks                   | Wireshark Filter or Clue                    | Detection Mindset                                       |
| --------------- | --------------------------------- | ------------------------------------------- | ------------------------------------------------------- |
| 1. Physical     | Cable tapping, jamming            | Not visible in Wireshark                    | Covered via physical audit or RF tools                  |
| 2. Data Link    | MAC spoofing, ARP spoofing        | `arp`, `eth.addr == XX:XX...`               | Sudden duplicate MAC, excessive ARP requests            |
| 3. Network      | IP spoofing, ICMP flood           | `icmp`, `ip.addr == x.x.x.x`                | Abnormal ICMP rate, conflicting IP headers              |
| 4. Transport    | TCP SYN flood, port scan          | `tcp.flags.syn == 1 and tcp.flags.ack == 0` | Lots of SYNs without ACKs                               |
| 5. Session      | Session hijack, replay attack     | `tcp.analysis.retransmission`               | Unusual session replays or re-sent ACKs                 |
| 6. Presentation | TLS downgrade, malformed encoding | `ssl`, `x.509`, `http contains "gzip"`      | Invalid certs, protocol downgrade from HTTPS            |
| 7. Application  | SQLi, XSS, C2 via HTTP            | `http.request`, `dns.qry.name`              | Suspicious URIs, encoded payloads, uncommon user-agents |



Reference:
1. https://unit42.paloaltonetworks.com/wireshark-tutorial-emotet-infection/
2. https://tryhackme.com/room/wiresharktrafficanalysis
