# Course 3 Lab Note: DNS & ICMP Traffic Analysis (`tcpdump`)

## Incident Summary
* **Timestamp:** `13:24:32.192571` (1:24 p.m.)[cite: 3]
* **Impacted Service / Port:** DNS over **UDP** port `53`[cite: 3]
* **Client IP:** `192.51.100.15`[cite: 3]
* **DNS Server IP:** `203.0.113.2`[cite: 3]
* **Target Domain:** `www.yummyrecipesforme.com`[cite: 3]

## Traffic & Packet Analysis
1. **Outbound DNS Query (UDP):** The client browser (`192.51.100.15`) sent a UDP DNS query to the DNS server (`203.0.113.2`) on port `53` requesting the IP address (`A` record) for `www.yummyrecipesforme.com`[cite: 3].
2. **Inbound Error Response (ICMP):** The DNS server replied with an ICMP `udp port 53 unreachable` error message, repeated three consecutive times[cite: 3].
3. **Interpretation:** Outbound network connectivity to `203.0.113.2` works, so the issue is not basic packet delivery—rather, no DNS service is actively listening on UDP port `53` or traffic to that port is being blocked/rejected[cite: 3].

## Detection & Investigation
* **How It Was Reported:** Customers of client companies reported being unable to reach `www.yummyrecipesforme.com` and saw a `destination port unreachable` error after the page timed out[cite: 3].
* **Analyst Actions:** An analyst reproduced the error by visiting the site and captured packets with `tcpdump` while retrying the request[cite: 3].

## Suspected Root Cause
The DNS service on `203.0.113.2` has stopped or crashed, or a firewall / ACL is blocking incoming UDP traffic on port `53`[cite: 3].

## Troubleshooting & Next Steps
1. **Check & Restart the DNS Service:** SSH into `203.0.113.2` and verify whether the DNS service (such as BIND or `systemd-resolved`) is active; restart it if stopped.
2. **Inspect Firewall Rules:** Check host firewall rules (`iptables` or `ufw`) to confirm UDP port `53` is allowed rather than dropped or rejected.
3. **Verify Resolution:** Re-test DNS queries and `tcpdump` capture after changes to confirm normal responses.
