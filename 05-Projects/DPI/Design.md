# Project 3 — Offline Deep Packet Inspection (DPI) / PCAP Analyzer

> **Language:** C++20/23  
> **Build:** CMake  
> **Platform:** Linux (Primary), Windows (Secondary)  
> **Type:** Offline Packet Analyzer & Protocol Inspector  
> **Target:** Wireshark-lite / Zeek-lite capable of parsing PCAP files, decoding common protocols, reconstructing flows, generating statistics and reports.

---

# 1. Overview

A modular Deep Packet Inspection engine that analyzes **offline PCAP captures** without live packet capture. The project parses packets layer-by-layer, reconstructs network flows, detects application protocols, and generates detailed reports.

Project Components

- PCAP Reader
- Packet Decoder
- Protocol Parsers
- Flow Tracker
- Statistics Engine
- Rule Engine
- Report Generator
- CLI Tool
- Benchmark Suite
- Unit Tests

---

# 2. Goals

- Fast packet parsing
- Modular protocol architecture
- Low memory usage
- Flow reconstruction
- Protocol detection
- Rule-based inspection
- Report generation
- Extensible parser design

---

# 3. Features

## PCAP

- Read PCAP files
- Validate headers
- Large file support
- Streaming parser

## Layer 2

- Ethernet II
- VLAN (optional)

## Layer 3

- IPv4
- IPv6 (optional)
- ICMP

## Layer 4

- TCP
- UDP

## Layer 7

- HTTP
- DNS
- TLS Detection
- FTP Detection
- SMTP Detection

## Analysis

- Flow reconstruction
- Packet statistics
- Top IPs
- Top Ports
- Bandwidth
- Conversations
- Protocol distribution

## Reports

- Console
- CSV
- JSON

---

# 4. Non Goals

- Live packet capture
- GUI
- IDS/IPS
- Firewall
- Packet modification
- Packet injection
- Distributed analysis

---

# 5. Technology Stack

| Component | Technology |
|------------|------------|
| Language | C++20/23 |
| Build | CMake |
| Tests | GoogleTest |
| Benchmark | Google Benchmark |
| JSON | nlohmann/json |
| Filesystem | std::filesystem |
| Time | chrono |
| Containers | STL |

---

# 6. Project Layout

```text
dpi/

├── CMakeLists.txt
├── README.md

├── include/
│   └── dpi/
│       ├── pcap.hpp
│       ├── packet.hpp
│       ├── ethernet.hpp
│       ├── ipv4.hpp
│       ├── tcp.hpp
│       ├── udp.hpp
│       ├── http.hpp
│       ├── dns.hpp
│       ├── flow.hpp
│       ├── analyzer.hpp
│       ├── report.hpp
│       ├── config.hpp
│       └── rule_engine.hpp

├── src/

├── apps/
│   └── dpi.cpp

├── tests/

├── benchmarks/

└── docs/
```

---

# 7. High-Level Architecture

```mermaid
flowchart LR

PCAP

--> Reader

--> Decoder

--> Protocol Parser

--> Flow Tracker

--> Analyzer

--> Report Generator
```

---

# 8. Parsing Pipeline

```mermaid
flowchart LR

PCAP

--> Ethernet

--> IPv4

--> TCP/UDP

--> Application Parser

--> Statistics
```

---

# 9. Core Components

## PCAP Reader

Responsibilities

- Read packets
- Validate PCAP
- Timestamp extraction
- Streaming reads

Public API

```cpp
open()

read_packet()

close()
```

---

## Packet Decoder

Responsibilities

- Decode packet headers
- Dispatch protocols
- Validate lengths
- Handle malformed packets

---

## Ethernet Parser

Parses

- Source MAC
- Destination MAC
- EtherType

Supports

- Ethernet II
- VLAN (optional)

---

## IPv4 Parser

Extract

- Source IP
- Destination IP
- TTL
- Flags
- Protocol
- Total Length

Validate

- Header checksum
- Header length

---

## TCP Parser

Extract

- Source Port
- Destination Port
- Sequence Number
- Acknowledgement
- Window Size
- TCP Flags

Flags

```
SYN

ACK

FIN

RST

PSH

URG
```

---

## UDP Parser

Extract

- Source Port
- Destination Port
- Length
- Checksum

---

## HTTP Parser

Extract

- Method
- URL
- Version
- Host
- User Agent
- Response Code
- Content Length

Methods

```
GET

POST

PUT

DELETE

HEAD
```

---

## DNS Parser

Extract

- Query
- Response
- Record Type
- Domain
- TTL

---

## Flow Tracker

Responsibilities

- Create flows
- Update packets
- Track bytes
- Track duration
- Close completed flows

Flow Key

```
Source IP

Destination IP

Source Port

Destination Port

Protocol
```

---

## Rule Engine

Responsibilities

- Match packets
- Match flows
- Detect signatures
- Raise alerts

Example Rules

```
HTTP Traffic

DNS Queries

TLS Connections

Large Transfers

Unknown Protocols
```

---

## Report Generator

Produces

- Summary
- CSV
- JSON
- Console output

---

# 10. Packet Structure

```cpp
Packet

Timestamp

Length

Headers

Payload
```

---

# 11. Internal Data Structures

```
Packet

↓

Protocol Headers

↓

Flow

↓

Statistics

↓

Reports
```

Containers

```
vector

unordered_map

deque

string_view
```

---

# 12. Thread Model

Initial Version

```
Single Thread
```

Future

```mermaid
flowchart LR

Reader

--> Queue

--> Worker 1

Worker 1 --> Analyzer

Queue --> Worker 2

Worker 2 --> Analyzer

Analyzer --> Reports
```

---

# 13. Memory Ownership

| Object | Owner |
|---------|------|
| Reader | Analyzer |
| Packet | Reader |
| Flow | Flow Tracker |
| Reports | Analyzer |

Guidelines

- RAII only
- No owning raw pointers
- Stream packets instead of storing all
- Reuse packet buffers where possible

---

# 14. Configuration

Example

```json
{
    "export":"json",
    "http":true,
    "dns":true,
    "tls":true,
    "flow_timeout":60,
    "report":"report.json"
}
```

---

# 15. CLI

Examples

```bash
dpi capture.pcap

dpi capture.pcap --summary

dpi capture.pcap --flows

dpi capture.pcap --http

dpi capture.pcap --dns

dpi capture.pcap --csv

dpi capture.pcap --json
```

---

# 16. Performance Targets

- >1M packets/sec
- Streaming parser
- Constant memory growth
- O(n) processing
- Zero packet copies where practical
- Fast protocol dispatch

---

# 17. Error Handling

Recoverable

- Malformed packet
- Unknown protocol
- Truncated packet
- Invalid checksum

Fatal

- Invalid PCAP
- Unsupported file format
- Corrupted capture header

Rules

- Never stop processing because of a malformed packet.
- Skip invalid packets and continue analysis.
- Produce useful diagnostics.

---

# 18. Coding Guidelines

- Modern C++20/23
- RAII
- `std::span`
- `std::string_view`
- `enum class`
- `constexpr`
- Exception-safe APIs
- Layer separation
- Zero unnecessary packet copies
- Modular protocol parsers

---

# 19. Future Extensions

- IPv6
- ARP
- DHCP
- ICMPv6
- QUIC
- HTTP/2
- HTTP/3
- TLS handshake parser
- Live capture (libpcap)
- IDS signatures
- Malware detection
- Plugin protocol architecture

---

# Part 2 (`DPI_IMPLEMENTATION.md`) will include

- Development roadmap (Phase 1–7)
- Dependency graph
- Benchmark methodology
- Testing strategy
- CI/CD
- AI implementation instructions
- Definition of Done
- Stretch goals