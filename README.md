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
## server.py
```
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)

print("Server start running... Waiting for connection")

c, addr = s.accept()
print("Connected to:", addr)

while True:
    client_message = c.recv(1024).decode()

    if client_message.lower() == "bye":
        print("Client disconnected")
        break

    print("Client: ", client_message)

    msg = input("Server: ")
    c.send(msg.encode())

    if msg.lower() == "bye":
        break

c.close()
s.close()

```
## client.py
```
import socket
s = socket.socket()
s.connect(('localhost', 8000))

print("Connected to server")

while True:
    msg = input("Client: ")
    s.send(msg.encode())

    if msg.lower() == "bye":
        break

    server_reply = s.recv(1024).decode()
    print("Server: ", server_reply)

    if server_reply.lower() == "bye":
        break

s.close()
```
## OUPUT
<img width="947" height="237" alt="image" src="https://github.com/user-attachments/assets/7e30767b-ba07-4361-81f9-3248916e7416" />

## RESULT
Thus, the python program for creating Chat using TCP Sockets Links was successfully 
created and executed.
