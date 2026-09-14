# Exercise 4: To Implement Socket Programming Using TCP/UDP

```
Name: Ranjith Ganesh B.
Reg No: 212223060222
```

## Aim

To implement **socket programming using TCP and UDP protocols** for communication between a client and a server.

---

# Algorithm

## TCP Socket Programming

### Server Side

1. **Start the program.**
2. Create a TCP socket using `SOCK_STREAM`.
3. Bind the socket to an IP address and port number.
4. Listen for incoming client connections.
5. Accept the client connection.
6. Receive data from the client.
7. Send a response to the client.
8. Close the connection and socket.
9. **Stop the program.**

### Client Side

1. **Start the program.**
2. Create a TCP socket.
3. Connect to the server using its IP address and port number.
4. Send data to the server.
5. Receive the server's response.
6. Display the received message.
7. Close the socket.
8. **Stop the program.**

---

## UDP Socket Programming

### Server Side

1. **Start the program.**
2. Create a UDP socket using `SOCK_DGRAM`.
3. Bind the socket to an IP address and port number.
4. Receive data from the client using `recvfrom()`.
5. Send a response using `sendto()`.
6. Close the socket.
7. **Stop the program.**

### Client Side

1. **Start the program.**
2. Create a UDP socket.
3. Send data to the server using `sendto()`.
4. Receive the server's response using `recvfrom()`.
5. Display the received message.
6. Close the socket.
7. **Stop the program.**

---

# Procedure for Executing the Program

1. Create a socket using Python's built-in `socket` module.
2. For TCP, create a stream socket using `SOCK_STREAM`.
3. For UDP, create a datagram socket using `SOCK_DGRAM`.
4. Bind the server socket to an IP address and port.
5. Start the server and wait for client communication.
6. Run the client and send a message.
7. Receive the response from the server.
8. Close the socket after communication.

---

# Program

## TCP Program

### TCP Server

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

server.bind(("localhost", 5000))
server.listen(1)

print("Waiting for connection...")

conn, addr = server.accept()

print("Connected:", addr)

data = conn.recv(1024).decode()
print("Client:", data)

conn.send("Hello from TCP Server".encode())

conn.close()
server.close()
```

### TCP Client

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

client.connect(("localhost", 5000))

client.send("Hello from TCP Client".encode())

data = client.recv(1024).decode()

print("Server:", data)

client.close()
```

---

## UDP Program

### UDP Server

```python
import socket

server = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

server.bind(("localhost", 5001))

print("Waiting for message...")

data, addr = server.recvfrom(1024)

print("Client:", data.decode())

server.sendto("Hello from UDP Server".encode(), addr)

server.close()
```

### UDP Client

```python
import socket

client = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

client.sendto(
    "Hello from UDP Client".encode(),
    ("localhost", 5001)
)

data, addr = client.recvfrom(1024)

print("Server:", data.decode())

client.close()
```

---

# Output

## TCP Server

<img width="848" height="167" alt="image" src="https://github.com/user-attachments/assets/6fb13417-b69d-4095-a3c1-cd2c1b7b9197" />


## TCP Client

<img width="788" height="80" alt="image" src="https://github.com/user-attachments/assets/13e2c128-7474-425d-b17d-f8afba259d4a" />


## UDP Server

<img width="802" height="115" alt="image" src="https://github.com/user-attachments/assets/5222215d-9107-4d69-a87c-e1af62b60e1b" />


## UDP Client

<img width="785" height="72" alt="image" src="https://github.com/user-attachments/assets/2243e7be-b02f-4135-bd8d-909322802efc" />

---

# Result

Thus, **socket programming using TCP and UDP** was successfully implemented, and communication between the **client and server** was established successfully.
