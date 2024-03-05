# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

```
Name : KEERTHI VASAN A
Reg.No : 212222240048
Date : 05.04.2024
```

## AIM
To write a python program for creating File Transfer using TCP Sockets Links
## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.
## PROGRAM

## CLIENT
```py
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello server!".encode())
with open('received_file', 'wb') as f:
 while True:
 print('receiving data...')
 data = s.recv(1024)
 print('data=%s', (data))
 if not data:
 break
 f.write(data)
f.close()
print('Successfully get the file')
s.close()
print('connection closed')
```
## SERVER
```py
import socket
port = 60000
s = socket.socket()
host = socket.gethostname()
s.bind((host, port)) 
s.listen(5)
while True:
 conn, addr = s.accept()
 data = conn.recv(1024)
 print('Server received', repr(data))
 filename='mytext.txt'
 f = open(filename,'rb')
 l = f.read(1024)
 while (l):
 conn.send(l)
 print('Sent ',repr(l))
 l = f.read(1024)
 f.close()
 print('Done sending')
 conn.send('Thank you for connecting'.encode())
 conn.close()
```
## OUTPUT

## CLIENT
![243812040-05bea753-f0d9-496b-9172-3ee87867c199](https://github.com/Jai-1801/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/139335300/bc546736-6408-4b8a-89b3-2c52438209b7)


## SERVER
![243812084-a850f5fb-1bc5-4e25-8f6a-19275c3106bb](https://github.com/Jai-1801/3c.FILE_TRANSFER_USING_TCP_SOCKETS/assets/139335300/b1a8a9b8-a98a-421c-838b-a04ec70f7a0c)

## RESULT
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
