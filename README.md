# MTP (My Transport Protocol) Socket Library

## Project Overview
This project implements a custom reliable transport protocol (MTP) built on top of unreliable UDP sockets, providing end-to-end reliable data transfer with flow control.

## Key Features
- Guaranteed message delivery in order
- Window-based flow control
- Simulated packet loss
- Support for up to 25 simultaneous MTP sockets

## Requirements
- Linux environment
- GCC compiler
- Make utility

## Implemented Functions
- `m_socket()`: Create an MTP socket
- `m_bind()`: Bind socket to local and remote addresses
- `m_sendto()`: Send messages reliably
- `m_recvfrom()`: Receive messages
- `m_close()`: Close MTP socket

## Configuration
Edit `msocket.h` to configure:
- `T`: Timeout duration (default 5 seconds)
- `p`: Packet loss probability (0.0 - 1.0)

## Testing
1. Compile the library:
```bash
make lib
```

2. Compile user applications:
```bash
make user1
make user2
```

3. Run initialization process:
```bash
./initmsocket
```

4. Run user applications in separate terminals:
```bash
./user1
./user2
```

## Performance Testing
- Vary packet loss probability (`p`) from 0.05 to 0.5
- Measure average message transmission attempts
- Results documented in `documentation.txt`

## Limitations
- Fixed message size (1 KB)
- Maximum 25 active sockets
- Supports only point-to-point communication

## Troubleshooting
- Ensure proper IP/Port configuration
- Check shared memory permissions
- Verify library linking

## Notes
- Implemented as a static library `libmsocket.a`
- Uses UDP sockets underneath
- Provides reliable, ordered message delivery
