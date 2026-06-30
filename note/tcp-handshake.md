# Three-Way TCP Handshake

## My Notes

The **Three-Way TCP Handshake** is the process TCP uses to establish a reliable connection before any data is sent between a client and a server.

I like to think of it as both devices introducing themselves and agreeing to communicate before exchanging information.

---

## Step 1: SYN

The client sends a **SYN (Synchronize)** packet to the server.

**Meaning:**  
> "I want to start a connection."

```
Client ---------------- SYN ----------------> Server
```

**Note:**
- Starts the TCP connection.
- Contains the client's initial sequence number.

---

## Step 2: SYN-ACK

The server replies with a **SYN-ACK** packet.

**Meaning:**  
> "I received your request, and I'm ready too."

```
Client <------------- SYN-ACK --------------- Server
```

**Note:**
- Acknowledges the client's SYN.
- Sends the server's own initial sequence number.

---

## Step 3: ACK

The client sends an **ACK (Acknowledgement)** packet.

**Meaning:**  
> "I got your response. We can start communicating."

```
Client ---------------- ACK ----------------> Server
```

**Note:**
- Confirms the server's response.
- The TCP connection is now established.

---

## Handshake Flow

```
Client                                      Server
   |                                           |
   |-------- SYN ----------------------------->|
   |                                           |
   |<------ SYN-ACK ---------------------------|
   |                                           |
   |-------- ACK ----------------------------->|
   |                                           |
   |      Connection Established               |
```

---

## Easy Way to Remember

```
SYN  →  SYN-ACK  →  ACK
```

Think of it like a conversation:

- **Client:** "Can we talk?"
- **Server:** "Yes, I can hear you."
- **Client:** "Great, let's begin."

---

## Why It Is Important

- Establishes a reliable connection.
- Makes sure both devices are ready to communicate.
- Synchronizes sequence numbers.
- Prevents communication issues caused by lost or duplicate packets.

---

## Quick Summary

| Step | Packet | What it Does |
|------|--------|--------------|
| 1 | SYN | Client requests a connection. |
| 2 | SYN-ACK | Server accepts and acknowledges the request. |
| 3 | ACK | Client confirms the connection. |

---

## Things I Should Remember

- TCP always uses the **Three-Way Handshake** before sending data.
- **SYN** starts the connection.
- **ACK** means "I received your message."
- Data transfer begins **only after** the final ACK is sent.
- Protocols like **HTTP, HTTPS, FTP, SSH, SMTP, POP3, and IMAP** all rely on TCP, so they use this handshake before communication starts.
