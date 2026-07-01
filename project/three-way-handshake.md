# TCP Three-Way Handshake Analysis

## Objective

The aim of this analysis is to observe how a TCP connection is established using Wireshark before any HTTPS communication takes place.

---

## Packet Summary

| Frame | Source IP | Destination IP | Source Port | Destination Port | TCP Flags |
|------:|------------|----------------|------------:|-----------------:|-----------|
| 773 | 172.20.10.2 | 131.253.33.254 | 27800 | 443 | SYN |
| 785 | 131.253.33.254 | 172.20.10.2 | 443 | 27800 | SYN, ACK |
| 786 | 172.20.10.2 | 131.253.33.254 | 27800 | 443 | ACK |

---

# Step 1: SYN Packet

**Frame 773**

The first packet is the **SYN** packet sent from the client (`172.20.10.2`) to the server (`131.253.33.254`). This is the client's way of requesting a connection with the server on **port 443**, which is used for HTTPS.

### Packet Details

- Source IP: `172.20.10.2`
- Destination IP: `131.253.33.254`
- Source Port: `27800`
- Destination Port: `443`
- TCP Flag: `SYN`
- Sequence Number: `0`

At this point, the client is simply asking the server if it is ready to communicate.

### Figure 1: SYN Packet

![SYN Packet](https://github.com/V-Adebayo/tcp-handshake-lab/blob/main/project/SYN.png)

---

# Step 2: SYN-ACK Packet

**Frame 785**

The server replies with a **SYN-ACK** packet. This tells the client that the connection request was received and that the server is ready to establish the connection.

### Packet Details

- Source IP: `131.253.33.254`
- Destination IP: `172.20.10.2`
- Source Port: `443`
- Destination Port: `27800`
- TCP Flags: `SYN, ACK`
- Sequence Number: `0`
- Acknowledgment Number: `1`

The acknowledgment number of **1** shows that the server received the client's SYN packet.

### Figure 2: SYN-ACK Packet

![SYN-ACK Packet](https://github.com/V-Adebayo/tcp-handshake-lab/blob/main/project/SYN-ACK.png)

---

# Step 3: ACK Packet

**Frame 786**

The client sends the last packet, which is the **ACK** packet. This confirms that it received the server's response.

### Packet Details

- Source IP: `172.20.10.2`
- Destination IP: `131.253.33.254`
- Source Port: `27800`
- Destination Port: `443`
- TCP Flag: `ACK`
- Sequence Number: `1`
- Acknowledgment Number: `1`

After this packet is sent, the TCP connection has been successfully established.

### Figure 3: ACK Packet

![ACK Packet](https://github.com/V-Adebayo/tcp-handshake-lab/blob/main/project/ACK.png)

---

# Complete TCP Three-Way Handshake

The packet capture shows all three packets used to establish the connection.

| Frame | Description |
|------:|-------------|
| 773 | Client sends SYN |
| 785 | Server replies with SYN-ACK |
| 786 | Client sends ACK |

### Figure 4: Complete TCP Three-Way Handshake

![TCP Three-Way Handshake](https://github.com/V-Adebayo/tcp-handshake-lab/blob/main/project/Three-way-handshake.png)

---

# What Happens Next?

After the TCP handshake is complete, the client starts the **TLS 1.3** handshake by sending a **Client Hello** message. The server responds with a **Hello Retry Request**, followed by a **Server Hello**. Once the TLS handshake is completed, both the client and the server begin exchanging encrypted application data.

This shows that TCP is responsible for creating the connection first, while TLS is responsible for securing the communication.

---

# Analysis

From the capture, the TCP Three-Way Handshake was completed successfully. The client first sent a SYN packet, the server replied with a SYN-ACK packet, and the client completed the process with an ACK packet. After the connection was established, the TLS 1.3 handshake began, followed by encrypted HTTPS traffic. This confirms that a TCP connection must be established before secure communication can take place.
