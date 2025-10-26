# EX.NO: 2c.SIMULATING ARP /RARP PROTOCOLS
## NAME - PRIYADARSHINI K
## REG NO - 212224100046
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
P
## PROGRAM - ARP
## client.py
```
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

## server.py
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
while True:
   ip=input("Enter logical Address : ")
   s.send(ip.encode())
   print("MAC Address",s.recv(1024).decode())
```

## OUPUT - ARP

## client.py
<img width="462" height="113" alt="image" src="https://github.com/user-attachments/assets/5383e011-a737-47e2-9b41-7db898152105" />

## server.py
<img width="630" height="242" alt="image" src="https://github.com/user-attachments/assets/b3830e2c-daa3-42b6-9f27-2f861fc20c3a" />


## PROGRAM - RARP
## client.py
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

## server.py
```
import socket
s=socket.socket()
s.connect(('localhost',9000))
while True:
   ip=input("Enter MAC Address : ")
   s.send(ip.encode())
   print(“Logical Address”, s.recv(1024).decode())
```


## OUPUT -RARP
## client.py
<img width="562" height="107" alt="image" src="https://github.com/user-attachments/assets/df4cc46f-be2a-4469-a074-1e54448c1545" />

## server.py
<img width="477" height="163" alt="image" src="https://github.com/user-attachments/assets/dd8316c8-8eaf-4ad2-ab47-161f8824a350" />



## RESULT
Thus, the python program for simulating ARP protocols using TCP was successfully 
executed.
