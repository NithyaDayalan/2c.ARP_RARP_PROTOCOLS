# 2c  SIMULATING ARP /RARP PROTOCOLS
## DEVELOPED BY : NITHYA D
## REG.NO : 212223240110

## AIM :
To write a python program for simulating ARP protocols using TCP.
## ALGORITHM :
### Client :
1. Start the program.
2. Using socket connection is established between client and server.
3. Get the IP address to be converted into MAC address.
4. Send this IP address to server.
5. Server returns the MAC address to client.
### Server :
1. Start the program.
2. Accept the socket which is created by the client.
3. Server maintains the table in which IP and corresponding MAC addresses are stored.
4. Read the IP address which is send by the client.
5. Map the IP address with its MAC address and return the MAC address to client.

## ARP :
### PROGRAM :
#### CLIENT :
```
Developed by : NITHYA D
Reg.no : 212223240110

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
#### SERVER :
```
Developed by : NITHYA D
Reg.no : 212223240110

import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
 ip=input("Enter logical Address : ")
 s.send(ip.encode())
 print("MAC Address",s.recv(1024).decode())
```
### OUPUT :
![image](https://github.com/NithyaDayalan/2c.ARP_RARP_PROTOCOLS/assets/166380061/00d85e1a-3b5c-4aa2-9237-cf9a3214ebba)

## RARP :
### PROGRAM :
#### CLIENT :
```
Developed by : NITHYA D
Reg.no : 212223240110

import socket
s=socket.socket()
s.bind(('localhost',9000))
s.listen(5)
c,addr=s.accept()
address={"6A:08:AA:C2":"192.168.1.100","8A:BC:E3:FA":"192.168.1.99"}
while True:
    ip=c.recv(1024).decode()
    try:
        c.send(address[ip].encode())
    except KeyError:
        c.send("Not found".encode())
```
#### SERVER :
```
Developed by : NITHYA D
Reg.no : 212223240110

import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
    ip=input("Enter mac address: ")
    s.send(ip.encode())
    print("Logical address",s.recv(1024).decode())
```
### OUTPUT :
![image](https://github.com/NithyaDayalan/2c.ARP_RARP_PROTOCOLS/assets/166380061/1f82fdcd-68dd-424e-97db-ac195e1f1a25)

## RESULT :
Thus, the python program for simulating ARP protocols using TCP was successfully executed.
