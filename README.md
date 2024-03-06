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
### Client :
```python
import socket
s=socket.socket()
s.bind(('localhost',8000))
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
### Server :
```python
import socket

s = socket.socket()
s.connect(('localhost', 8000))
while True:
    print(s.recv(1024).decode())
    s.send("acknowledgement recived from the server".encode())
```
## OUPUT
### Client :
![WhatsApp Image 2024-03-06 at 11 25 17 AM](https://github.com/JEGADEESH07/2b_SLIDING_WINDOW_PROTOCOL/assets/113497131/34e2ab20-440c-4c25-9c0d-890bc33d1ac3)
### Server :
![WhatsApp Image 2024-03-06 at 11 25 17 AM(1)](https://github.com/JEGADEESH07/2b_SLIDING_WINDOW_PROTOCOL/assets/113497131/90b5f9fc-0b83-46df-a17a-fdf91ef1ba60)

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
