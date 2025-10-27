# 3c.CREATION FOR FILE TRANSFER USING TCP SOCKETS

## AIM
To write a python program for creating File Transfer using TCP Sockets Links

## ALGORITHM:
1. Import the necessary python modules.
2. Create a socket connection using socket module.
3. Send the message to write into the file to the client file.
4. Open the file and then send it to the client in byte format.
5. In the client side receive the file from server and then write the content into it.

## PROGRAM

### Client:
```
import socket
s = socket.socket()
host = socket.gethostname()
port = 60000
s.connect((host, port))
s.send("Hello Server".encode())
with open("received_file", "wb") as f:
    while True:
        print('receiving data...')
        data = s.recv(1024)
        print('data=%s' % data)
        if not data:
            break
        f.write(data)
    print('Successfully got the file')
    s.close()
    print('connection closed')
```

### Server:
```
import socket
port=60000
s=socket.socket()
host=socket.gethostname()
s.bind((host,port))
s.listen(5)
while True:
    conn,addr=s.accept()
    data=conn.recv(1024)
    print("Server received",repr(data))
    filename='mytext.txt'
    f=open(filename,'rb')
    l=f.read(1024)
    while (l):
        conn.send(l)
        print('Sent ',repr(l))
        l=f.read(1024)

    f.close()
    print("Done sending")
    conn.send('Thank you for connecting'.encode())
    conn.close()
```

## OUTPUT:

### Client:
<img width="1359" height="253" alt="Screenshot 2025-10-27 103529" src="https://github.com/user-attachments/assets/da40a0c0-02f0-4b5f-9342-2554c5199d05" />

### Server:
<img width="1329" height="189" alt="Screenshot 2025-10-27 103456" src="https://github.com/user-attachments/assets/649f9bdf-31b2-4e63-95df-4945f4344f53" />

## RESULT:
Thus, the python program for creating File Transfer using TCP Sockets Links was 
successfully created and executed.
