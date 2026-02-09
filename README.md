# TCP Client–Server (ACK Echo + Status)

## Overview
This project implements a simple **TCP** client and server using Python sockets.

- The **server** listens on port **2222**, accepts TCP connections, assigns each client a unique name (e.g., `Client01`), and echoes back messages with `"ACK"` appended.
- The **client** connects to the server, receives its assigned name, sends it back for confirmation, then repeatedly sends user input to the server.

## Features
### 1) ACK Echo
Any normal message sent from the client is returned by the server with `"ACK"` appended.

Example:
- Client sends: `hello`
- Server replies: `helloACK`

### 2) Client Naming
When a client connects:
1. Server sends a unique name to the client.
2. Client prints the name and sends it back.

### 3) Status Command
If the client types `status`, the server returns a summary of client connection info (connected time and disconnected time if applicable).

### 4) Exit Command
If the client types `exit`, the client sends `exit` to the server and closes the connection.

## How it works (TCP)
- Uses `socket(AF_INET, SOCK_STREAM)` which is **TCP** (connection-oriented, reliable, ordered delivery).
- Server uses:
  - `bind()` to attach to port 2222
  - `listen(3)` to allow up to 3 queued connections
  - `accept()` to create a dedicated socket per connected client
- Client uses:
  - `connect()` to create a TCP connection to the server

## Requirements
- Python 3.x
- No external packages needed

## Running the program
### Terminal 1: Start the server
```bash
python server.py
