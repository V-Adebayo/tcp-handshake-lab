# TCP Three-Way Handshake Analysis using Wireshark

## Overview

This project analyzes the TCP Three-Way Handshake using Wireshark. The capture shows how a TCP connection is established before encrypted HTTPS communication begins.

The packets were captured during a connection between a client and a server communicating over port 443 (HTTPS).

---

## Objective

The objective of this project is to:

- Capture TCP traffic using Wireshark.
- Identify the three packets involved in the TCP Three-Way Handshake.
- Explain the purpose of each packet.
- Observe what happens immediately after the handshake.

---

## Tools Used

- Wireshark
- Windows
- HTTPS Traffic (TLS 1.3)

---

## Files Included

```
TCP-Three-Way-Handshake/
│
├── README.md
├── report.md
└── screenshots/
    ├── SYN.png
    ├── SYN-ACK.png
    ├── ACK.png
    └── Three-ways-handshake.png
```

---

## Packet Flow

1. Client sends **SYN**
2. Server replies with **SYN-ACK**
3. Client sends **ACK**
4. TLS handshake begins
5. Encrypted application data is exchanged

---

## What I Learned

Working on this project helped me understand that TCP creates a reliable connection before any application data is exchanged. I also observed that HTTPS traffic starts with a TLS handshake immediately after the TCP connection has been established.

---

## Conclusion

The Wireshark capture confirms that a TCP connection is established using the standard three-way handshake before secure HTTPS communication begins.
