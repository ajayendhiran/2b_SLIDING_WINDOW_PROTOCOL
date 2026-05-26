# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
```
client.py
s=socket.socket() 
s.bind(('localhost',7000)) 
s.listen(5) 
c,addr=s.accept() 
size=int(input("Enter number of frames to send : ")) 
l=list(range(size)) 
s=int(input("Enter Window Size : ")) 
st=0 
i=0 
while True: 
    while(i<len(l)):
        st+=s 
        c.send(str(l[i:st]).encode()) 
        ack=c.recv(1024).decode() 
        if ack:
            print(ack) 
            i+=s
```
```
server.py
import socket 
s=socket.socket() 
s.connect(('localhost',7000)) 
while True: 
    print(s.recv(1024).decode()) 
    s.send("acknowledgement recived from the server".encode())
```

## OUPUT
<img width="1920" height="1019" alt="{AC0F551E-4FFC-41EA-98B9-A7219DF87243}" src="https://github.com/user-attachments/assets/a1ded71f-978f-46df-8757-f8865f12cd1c" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
