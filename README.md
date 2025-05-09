
Two-Stage Client-Server Communication using TCP & UDP in Virtualized Environments
==================================================================================

Overview:
---------
This project implements a two-stage client-server communication system using both TCP and UDP sockets,
written in C++. It is designed to analyze socket communication in various virtualized environments like
WSL and Ubuntu VM. The system includes:

- A multi-threaded server supporting both FCFS and Round-Robin scheduling.
- A client that communicates using a TCP-initiated negotiation followed by UDP data transfer.
- Performance benchmarking for throughput across various message sizes and host-VM configurations.

Features:
---------
- Stage 1 (TCP): Client requests UDP port; Server responds with a port.
- Stage 2 (UDP): Data transfer via the negotiated port.
- Concurrent server with thread-based request handling.
- Two scheduling policies:
    - FCFS (First Come First Serve)
    - Round Robin
- Performance measurement and graph generation for:
    - Throughput (TCP and UDP)
    - Transfer time for large messages (1MB to 10MB)

Files Included:
---------------
- server.cpp     : Multi-threaded TCP/UDP server
- client.cpp     : Client for TCP negotiation and UDP data exchange
- Assignment_4b_Group14_Report.pdf : Detailed report and analysis
- CS558_4b__Socket_Programming_VM.pdf : Assignment brief

How to Compile:
---------------
Use the following commands:

    g++ -pthread server.cpp -o server
    g++ client.cpp -o client

How to Run:
-----------
Server:
    ./server <UDP_PORT> <scheduling_policy>
    - <UDP_PORT>: Port for UDP communication
    - <scheduling_policy>: 'f' for FCFS, 'r' for Round-Robin

Example:
    ./server 9090 f

Client:
    ./client <SERVER_IP> <TCP_PORT>

You will be prompted to enter the payload size for testing throughput.

Example:
    ./client 192.168.56.101 8080

Output:
-------
Client generates two CSV files:
- tcp.txt  : TCP throughput data
- udp.txt  : UDP throughput data

Use these files to plot performance graphs using tools like Python or Excel.

Dependencies:
-------------
- C++ Standard Libraries
- POSIX threads (pthread)
- Socket programming libraries

Observations:
-------------
- UDP had better throughput for small messages compared to TCP.
- Round-Robin scheduling ensured fairness across multiple clients.
- Bridged networking enabled successful communication between host and VM.
- NAT configuration in WSL limited communication unless configured properly.

Authors:
--------
Group 14 – CS558: Computer Systems Lab
IIT Guwahati, Spring 2025

License:
--------
This project is intended solely for academic use under CS558 guidelines.
