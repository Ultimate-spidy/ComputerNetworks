# Computer Networks Lab - Final Submission

**Roll Number:** 231210059

This repository contains all the lab assignments completed for the Computer Networks course. The labs cover various networking concepts including socket programming, network topologies, NAT configuration, and IPv6 addressing.

---

## Repository Structure

```
├── Lab1_ping.docx              # Lab 1: Ping Command Documentation
├── lab2/                       # Lab 2: Basic TCP Socket Programming
│   ├── Client_231210059.c
│   └── Server_231210059.c
├── lab3/                       # Lab 3: Multi-threaded Server (Reader-Writer)
│   ├── Client_231210059.c
│   └── server_231210059.c
├── multiClientServer_231210059.c   # Multi-Client Server (Fork-based)
├── topologies/                 # Network Topologies (Packet Tracer)
│   ├── all_Topo.pkt
│   ├── bus_topo.pkt
│   ├── mesh_topo.pkt
│   ├── ring_topo.pkt
│   ├── star_topo.pkt
│   └── topo.pkt
├── NAT.pkt                     # NAT Configuration
├── my_nat.pkt                  # Custom NAT Configuration
├── connect2lan_router.pkt      # LAN Router Configuration
├── ipv6_Add.pkt                # IPv6 Addressing Configuration
└── peer2peer.pkt               # Peer-to-Peer Network Configuration
```

---

## Lab 1: Ping Command

**File:** `Lab1_ping.docx`

This lab covers the fundamentals of the `ping` command, which is used to test the reachability of a host on an IP network and measure the round-trip time for messages.

---

## Lab 2: Basic TCP Client-Server Socket Programming

**Files:** `lab2/Client_231210059.c`, `lab2/Server_231210059.c`

### Description
A basic TCP client-server implementation demonstrating fundamental socket programming concepts in C.

### Server Features
- Creates a TCP socket and binds to port 8080
- Listens for incoming connections
- Accepts a single client connection
- Receives messages from the client and echoes back a response
- Uses `SO_REUSEADDR` and `SO_REUSEPORT` socket options

### Client Features
- Connects to the server at a specified IP address on port 8080
- Sends a message to the server
- Receives and displays the server's response

### How to Compile and Run

```bash
# Compile
gcc lab2/Server_231210059.c -o server
gcc lab2/Client_231210059.c -o client

# Run Server (in terminal 1)
./server

# Run Client (in terminal 2)
./client
```

---

## Lab 3: Multi-threaded Server with Reader-Writer Pattern

**Files:** `lab3/server_231210059.c`, `lab3/Client_231210059.c`

### Description
A multi-threaded server implementation using POSIX threads (pthreads) and semaphores to handle concurrent client connections with the Reader-Writer synchronization pattern.

### Server Features
- Uses semaphores for synchronization between readers and writers
- Supports up to 50 concurrent connections
- Implements the Reader-Writer problem:
  - Multiple readers can access simultaneously
  - Writers have exclusive access
- Listens on port 8989
- Creates separate threads for readers and writers based on client choice

### Client Features
- Interactive client with continuous message sending capability
- Connects to the server (Note: Client is configured for port 8080, server runs on port 8989 - adjust as needed)
- Sends user input to the server
- Displays echoed responses from the server
- Supports graceful exit with "exit" command

### How to Compile and Run

```bash
# Compile Server (with pthread library)
gcc lab3/server_231210059.c -o server_threaded -lpthread

# Compile Client
gcc lab3/Client_231210059.c -o client_interactive

# Run Server (in terminal 1)
./server_threaded

# Run Client (in terminal 2)
./client_interactive
```

---

## Multi-Client Server (Fork-based)

**File:** `multiClientServer_231210059.c`

### Description
A concurrent server implementation using the `fork()` system call to handle multiple clients simultaneously. Each client connection is handled by a separate child process.

### Features
- Fork-based concurrency model
- Handles multiple clients simultaneously
- Echo server functionality - reflects received messages back to clients
- Prevents zombie processes using `SIGCHLD` signal handling
- Listens on port 8080
- Buffer size of 1024 bytes

### How to Compile and Run

```bash
# Compile
gcc multiClientServer_231210059.c -o multi_server

# Run
./multi_server
```

You can connect multiple clients using tools like `telnet` or `nc`:
```bash
# Using netcat
nc localhost 8080

# Using telnet
telnet localhost 8080
```

---

## Network Topologies (Cisco Packet Tracer)

**Directory:** `topologies/`

This directory contains Cisco Packet Tracer files demonstrating various network topologies:

| File | Description |
|------|-------------|
| `star_topo.pkt` | Star topology - all devices connected to a central hub/switch |
| `bus_topo.pkt` | Bus topology - all devices connected to a single communication line |
| `ring_topo.pkt` | Ring topology - devices connected in a circular fashion |
| `mesh_topo.pkt` | Mesh topology - every device connected to every other device |
| `all_Topo.pkt` | Combined demonstration of all topologies |
| `topo.pkt` | Additional topology configuration |

### How to View
Open these files using **Cisco Packet Tracer** software.

---

## Network Configuration Files (Cisco Packet Tracer)

### NAT Configuration
**Files:** `NAT.pkt`, `my_nat.pkt`

Demonstrates Network Address Translation (NAT) configuration, which allows multiple devices on a private network to share a single public IP address.

### LAN Router Configuration
**File:** `connect2lan_router.pkt`

Configuration for connecting two LANs using a router.

### IPv6 Addressing
**File:** `ipv6_Add.pkt`

Demonstrates IPv6 address configuration and networking.

### Peer-to-Peer Network
**File:** `peer2peer.pkt`

Configuration for a peer-to-peer network setup.

---

## Technologies Used

- **Programming Language:** C
- **Networking:** TCP/IP Sockets (POSIX)
- **Concurrency:** POSIX Threads (pthreads), Fork, Semaphores
- **Network Simulation:** Cisco Packet Tracer
- **Operating System:** Linux/Unix

---

## Prerequisites

- GCC Compiler
- Linux/Unix environment (for socket programming)
- Cisco Packet Tracer (for viewing .pkt files)

---

## Author

**Roll Number:** 231210059

This repository represents the final submission for the Computer Networks Lab course.
