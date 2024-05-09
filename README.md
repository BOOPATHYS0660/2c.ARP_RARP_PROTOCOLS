# Ex No :2c SIMULATING ARP /RARP PROTOCOLS
## NAME : ARAVINDAN D
## REGISTER NUMBER : 212223240012
## AIM
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
## PROGRAM - ARP
### CLIENT
```py
import socket
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
c,addr=s.accept()
address={"165.165.80.80":"6A:08:AA:C2","165.165.79.1":"SA:BC:E3:FA"};
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode()) 
    except KeyError:
        c.send("Not Found".encode())

```
### SERVER
```py
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address: ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())

```
## OUPUT - ARP
### CLIENT OUTPUT
![Screenshot 2024-05-09 124830](https://github.com/Aravindan2006/2c.ARP_RARP_PROTOCOLS/assets/151760062/d1ced85c-64b8-4e9a-b9cb-99f0388feb68)

### SERVER OUTPUT
![Screenshot 2024-05-09 124838](https://github.com/Aravindan2006/2c.ARP_RARP_PROTOCOLS/assets/151760062/208b6429-b0f6-4340-981d-86c7b34110bc)

## PROGRAM - RARP
### CLIENT
```py
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
### SERVER
```py
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
 ip=input("Enter MAC Address : ")
 s.send(ip.encode())
 print("Logical Address",s.recv(1024).decode())
```
## OUPUT -RARP
### CLIENT OUTPUT
![Screenshot 2024-05-09 125346](https://github.com/Aravindan2006/2c.ARP_RARP_PROTOCOLS/assets/151760062/8d72a2f1-5205-47c5-b664-01e3ef49c03b)

### SERVER OUTPUT
![Screenshot 2024-05-09 125355](https://github.com/Aravindan2006/2c.ARP_RARP_PROTOCOLS/assets/151760062/b4dd4535-91d5-47aa-b952-65b395b10027)

## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
