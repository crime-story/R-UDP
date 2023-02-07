# Reliable User Datagram Protocol (RUDP)

This project aims to implement the RUDP protocol over the UDP header. The UDP header consists of 4 fields: source and destination port, checksum, and header length. The first 5 bytes of the payload will be used to represent the RUDP header, which will contain the following fields:

- Sequence number (2 bytes)
- Acknowledgement number (2 bytes)
- Flags (SYN, SEQ, ACK, PSH, FIN) - the first 5 bits of the 5th byte of the header, with the remaining 3 unused.

The project will include a client and a server for RUDP that can perform the following tasks:

- A 3-way handshake at the beginning of the connection, like TCP
- Sending packets in a reliable manner (simulated by the packet loss command to work correctly, i.e. send 10 packets with 40% packet loss, lost packets are resent, and the server receives a total of 10 packets, so I can also verify that it works) using SEQ and ACK like TCP
- Correctly set flags (SYN when the connection starts, PUSH when data is sent, FIN when the connection is to be closed)
- Close the connection with FIN, like TCP

Notes:

- The data sent will be less than 100 bytes in size to avoid data fragmentation
- The sequence number must be unique for each packet (however you like, in ascending order, uint16 (sha256 (unixtimestamp + last sequence no)), etc.)
- The client has a different sequence number from the server

Explanation: We use UDP, all these processing is done in the UDP payload at the application layer.



### **Running the program in terminal**:
```
sudo docker-compose up -d 
```

```
sudo docker-compose exec receptor bash -c "python3 /elocal/src/server.py -p 10000 -f /elocal/src/date.out" 
```

```
sudo docker-compose exec emitator bash -c "python3 /elocal/src/client.py -a 198.8.0.2 -p 10000 -f /elocal/src/date.in" 
```
