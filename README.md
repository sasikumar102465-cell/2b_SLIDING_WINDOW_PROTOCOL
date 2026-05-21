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
## Client
~~~
#Developed by: SASIKUMAR S
#Register number: 212225100046
import socket
s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()
size = int(input("Enter number of frames to send : "))
l = list(range(size))
ws = int(input("Enter Window Size : "))
st = 0
i = 0
while True:
    while i < len(l):
        st = i + ws
        c.send(str(l[i:st]).encode())
        ack = c.recv(1024).decode()
        if ack:
            print(ack)
            i += ws
    break
~~~
## Server
~~~
#Developed by: SASIKUMAR S
#Register number: 212225100046
import socket
s = socket.socket()
s.connect(('localhost', 8000))
while True:
    data = s.recv(1024).decode()
    if not data:
        break
    print(data)
    s.send("Acknowledgement received from client".encode())
s.close()
~~~
## OUPUT
<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/b19fcb14-8ca7-440d-836c-a60d84af9ff0" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed
