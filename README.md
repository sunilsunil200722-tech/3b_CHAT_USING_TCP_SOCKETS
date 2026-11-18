# 3b.CREATION FOR CHAT USING TCP SOCKETS
## AIM
To write a python program for creating Chat using TCP Sockets Links.
## ALGORITHM:
1. Import the necessary modules in python
2. Create a socket connection to using the socket module.
3. Send message to the client and receive the message from the client using the Socket module in
 server
4. Send and receive the message using the send function in socket.

## PROGRAM

### server code:
```
import socket

# Create socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind host and port
host = '127.0.0.1'
port = 5000

server_socket.bind((host, port))

# Listen for client
server_socket.listen(1)

print("Waiting for client connection...")

# Accept connection
client_socket, addr = server_socket.accept()

print("Connected to:", addr)

while True:
    # Receive message from client
    client_message = client_socket.recv(1024).decode()

    print("Client:", client_message)

    # Exit condition
    if client_message.lower() == "bye":
        break

    # Send message to client
    message = input("Server: ")

    client_socket.send(message.encode())

    if message.lower() == "bye":
        break

# Close connection
client_socket.close()
server_socket.close()
```

### client code:
```
import socket

# Create socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Server details
host = '127.0.0.1'
port = 5000

# Connect to server
client_socket.connect((host, port))

print("Connected to server")

while True:
    # Send message to server
    message = input("Client: ")

    client_socket.send(message.encode())

    if message.lower() == "bye":
        break

    # Receive message from server
    server_message = client_socket.recv(1024).decode()

    print("Server:", server_message)

    if server_message.lower() == "bye":
        break

# Close connection
client_socket.close()
```
## OUPUT

### server output:
<img width="1202" height="677" alt="Screenshot 2026-11-18 082451" src="https://github.com/user-attachments/assets/c1310a14-c6b6-4239-90bd-671b0f856f77" />

### client output:
<img width="1201" height="677" alt="Screenshot 2026-11-18 082515" src="https://github.com/user-attachments/assets/9c41e091-54e7-4c86-8afa-2f6b3790a421" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
