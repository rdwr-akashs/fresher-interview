# Networking Questions and Answers

## 1. What is the OSI model? Name its layers.
The OSI (Open Systems Interconnection) model is a conceptual framework used to understand and implement network protocols in seven layers. It helps in standardizing network communication.

**Layers of OSI model:**
1. **Physical Layer** – Transmits raw bitstream over the physical medium.
2. **Data Link Layer** – Ensures node-to-node data transfer and handles error correction.
3. **Network Layer** – Handles routing and forwarding (e.g., IP).
4. **Transport Layer** – Ensures reliable data transfer (e.g., TCP).
5. **Session Layer** – Manages sessions and controls dialogues between computers.
6. **Presentation Layer** – Translates data formats (encryption, compression).
7. **Application Layer** – Interfaces directly with the end-user (e.g., HTTP, FTP).

---

## 2. Explain the difference between OSI and TCP/IP models.

The OSI (Open Systems Interconnection) and TCP/IP (Transmission Control Protocol/Internet Protocol) models are two reference models used to understand and design computer networks. While OSI is a theoretical model, TCP/IP is a practical model that is widely used in real-world networking.

### Key Differences:

| Feature                    | OSI Model                                   | TCP/IP Model                              |
|---------------------------|---------------------------------------------|-------------------------------------------|
| **Full Form**             | Open Systems Interconnection                | Transmission Control Protocol/Internet Protocol |
| **Development**           | Developed by ISO                            | Developed by DARPA (U.S. DoD)              |
| **Number of Layers**      | 7 Layers                                    | 4 Layers                                   |
| **Layers**                | Application, Presentation, Session, Transport, Network, Data Link, Physical | Application, Transport, Internet, Network Access |
| **Functionality**         | Describes what each layer should do         | Describes standard protocols and how they interact |
| **Approach**              | Layered and strictly defined                | Protocol-based and more flexible           |
| **Usage**                 | Conceptual/reference model                  | Implementation/real-world communication   |
| **Protocol Dependency**   | Protocol-independent                        | Protocol-oriented (focuses on TCP/IP)     |
| **Model Structure**       | Theoretical and descriptive                 | Practical and prescriptive                 |

### Summary:
- The OSI model is primarily used as a teaching tool to explain networking concepts and the different layers of data communication.
- The TCP/IP model, on the other hand, is the foundation of the modern internet and guides actual data transmission across networks.

Although both models serve similar purposes, they differ in structure, implementation, and practical use.

---

## 3. What is TCP and how is it different from UDP?
**TCP (Transmission Control Protocol)** is a connection-oriented protocol that provides reliable, ordered, and error-checked delivery of data.

**UDP (User Datagram Protocol)** is a connectionless protocol that offers faster data transmission but without guarantee of delivery, order, or error-checking.

| Feature | TCP | UDP |
|--------|-----|-----|
| Connection | Connection-oriented | Connectionless |
| Reliability | Reliable | Unreliable |
| Speed | Slower | Faster |
| Use Case | Web, Email, File Transfer | Streaming, VoIP, Online Games |

---

## 4. What is the three-way handshake in TCP?
The three-way handshake is a process used in TCP to establish a connection between a client and a server.

**Steps:**
1. **SYN**: Client sends a synchronization request to the server.
2. **SYN-ACK**: Server acknowledges and sends its own SYN.
3. **ACK**: Client sends an acknowledgment back to the server.

This ensures a reliable connection is established before data transmission begins.

---

## 5. What is IPv4 and IPv6?
- **IPv4 (Internet Protocol version 4)**: A 32-bit address format (e.g., 192.168.1.1) that supports around 4.3 billion addresses.
- **IPv6 (Internet Protocol version 6)**: A 128-bit address format (e.g., 2001:0db8:85a3::8a2e:0370:7334) that supports a vastly larger number of unique IP addresses.

**IPv6 Advantages:**
- Larger address space
- Built-in security
- Better routing efficiency

---

## 6. What is classful and classless addressing?
- **Classful Addressing**: IP addresses are divided into fixed classes (A, B, C, D, E). Each class has a default subnet mask and a fixed number of networks and hosts.
- **Classless Addressing (CIDR)**: Uses variable-length subnet masking (VLSM) to allocate IP addresses more efficiently. No rigid classes; supports hierarchical routing.

Example: `192.168.1.0/24` instead of relying on class rules.

---

## 7. What is a subnet mask?
A subnet mask is used to divide an IP address into network and host portions. It helps determine which part of the IP address identifies the network and which part identifies the host.

Example:  
IP Address: `192.168.1.10`  
Subnet Mask: `255.255.255.0`  
Network: `192.168.1.0`  
Host: `10`

---

## 8. What is MAC address? How is it different from an IP address?
- **MAC (Media Access Control) address**: A unique hardware identifier assigned to a network interface card (NIC). Example: `00:1A:2B:3C:4D:5E`
- **IP Address**: A logical address assigned to a device for network communication.

**Differences:**
| Feature | MAC Address | IP Address |
|--------|-------------|------------|
| Type | Physical address | Logical address |
| Assigned by | Manufacturer | Network Administrator / DHCP |
| Format | Hexadecimal | Decimal (IPv4) or Hexadecimal (IPv6) |
| Scope | Local Network | Global Network |
