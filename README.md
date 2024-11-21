# Ex No :3b PROGRAM FOR REVERSE ADDRESS RESOLUTION PROTOCOL(RARP) USING UDP 
## AIM:
To write a python program for simulating RARP protocols using UDP 
## ALGORITHM:
## Client:
1. Start the program 
2. Using datagram sockets UDP function is established. 
3. Get the MAC address to be converted into IP address. 
4. Send this MAC address to server. 
5. Server returns the IP address to client. 
## Server:
1. Start the program. 
2. Server maintains the table in which IP and corresponding MAC addresses are stored. 
3. Read the MAC address which is send by the client. 
4. Map the IP address with its MAC address and return the IP address to client.
## PROGRAM:
### CLIENT:
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
### SERVER:
```
import socket 
s=socket.socket() 
s.connect(('localhost',9000)) 
while True: 
    ip=input("Enter MAC Address : ") 
    s.send(ip.encode()) 
    print("Logical Address",s.recv(1024).decode()) 

```
## OUTPUT:
### CLIENT 
![Screenshot 2024-11-21 184952](https://github.com/user-attachments/assets/5da93ceb-c23f-452a-af9e-bc58a5781158)


### SERVER
![Screenshot 2024-11-21 184935](https://github.com/user-attachments/assets/3f11a940-a0cd-4a26-ac9a-b80f1ed9220f)


## RESULT
Thus, python program for simulating RARP protocols using UDP was successfully executed. 
