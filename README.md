# 2c.SIMULATING ARP /RARP PROTOCOLS

## AIM:
To write a python program for simulating ARP protocols using TCP.

## ALGORITHM:
## Client:
1. Start the program
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
## Server:
1. Start the program
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are
stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## PROGRAM - ARP:
### Client
```
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"8A:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Server
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
    ip=input("Enter logical Address : ")
    s.send(ip.encode())
    print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP:
### Client
![313178235-e9bf8a9b-cf18-42e2-8e3c-3aa67cad236f](https://github.com/Priya-Loganathan/2c.ARP_RARP_PROTOCOLS/assets/121166075/d402f3cc-a911-4c7a-b7ee-a74f9c5adcd1)
### Server
![313178289-5fb6c7c9-96ab-449d-abf7-63ec3f86bb18](https://github.com/Priya-Loganathan/2c.ARP_RARP_PROTOCOLS/assets/121166075/a6e764d7-67aa-4aff-ae8e-8dc34b38a3d9)

## PROGRAM - RARP:
### Client
```
import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not Found".encode())
```
### Server
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter MAC Address : ")
    s.send(ip.encode())
    print("Logical Address",s.recv(1024).decode())
```

## OUPUT -RARP:
### Client
![313178384-d4db0f9d-1d91-474d-8afd-47fe47453ea6](https://github.com/Priya-Loganathan/2c.ARP_RARP_PROTOCOLS/assets/121166075/89c7386f-30b3-4de9-a716-238319fea153)

### Server
![313178432-0b8f12ae-b52b-43f8-8a6a-c83185d84a0e](https://github.com/Priya-Loganathan/2c.ARP_RARP_PROTOCOLS/assets/121166075/08bb5821-5f59-4514-91a7-ee3cb9ff553a)

## RESULT:
Thus, the python program for simulating ARP protocols using TCP was successfully executed.
