# ICMP Helper Library

A Python implementation of ICMP echo requests and traceroute functionality using raw sockets.

This project explores low-level network communication by manually constructing, sending, and parsing ICMP packets rather than relying on system utilities such as `ping` or `traceroute`.

## Features

- Manually builds ICMP echo request packets
- Calculates ICMP checksums
- Sends packets using raw sockets
- Parses ICMP echo replies
- Validates:
  - Packet identifiers
  - Sequence numbers
  - Returned payload data
- Implements ping-style statistics:
  - Packet loss percentage
  - Minimum round-trip time
  - Average round-trip time
  - Maximum round-trip time
- Implements traceroute functionality using TTL manipulation
- Handles ICMP responses including:
  - Echo replies
  - Time exceeded messages
  - Destination unreachable messages

## How It Works

The library creates ICMP packets directly using Python's `socket` and `struct` libraries.

The packet workflow:

1. Create an ICMP echo request
2. Build the packet header
3. Encode timestamp and payload data
4. Calculate the ICMP checksum
5. Send the packet through a raw socket
6. Receive ICMP responses
7. Parse and validate returned packet data

Traceroute functionality is implemented by incrementally increasing the packet TTL value. Routers along the path return ICMP "Time Exceeded" messages, allowing the route to the destination to be discovered hop-by-hop.

## Requirements

- Python 3
- Linux environment recommended
- Root privileges required for raw socket access

## Usage

Run the script with elevated privileges:

```bash
sudo python3 IcmpHelperLibrary.py

The target host can be changed in the main() function:
icmpHelperPing.traceRoute("8.8.8.8")

Example operations:
icmpHelperPing.sendPing("google.com")
icmpHelperPing.traceRoute("google.com")

## Technical Concepts Demonstrated
The project demonstrates:
- Network programming with Python sockets
- ICMP protocol structure
- Binary data packing and unpacking with struct
- Raw packet manipulation
- Internet Protocol TTL behavior
- Round-trip time measurment
- Packet validation techniques
- Network Diagnostic tool implementation

## Notes
This implementation was created as part of networking coursework and focuses on understanding the mechanisms behind common network diagnostic tools.

Rather than invoking existing operating system utilities, this project works directly with the ICMP protocol by constructing packets, sending them through raw sockets, and interpreting network responses.

It is intended for educational use and experimentation with network protocols.
