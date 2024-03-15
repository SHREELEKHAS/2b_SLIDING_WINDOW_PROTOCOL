## SHREE LEKHA.S 212223110052
# 2b IMPLEMENTATION OF SLIDING WINDOW PROTOCOL
## AIM:
To write a python program to perform implementation of sliding window protocol
## ALGORITHM:
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM:
### client:
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(5)
c, addr = s.accept()

size = int(input("Enter number of frames to send: "))
frames = list(range(size))
window_size = int(input("Enter Window Size: "))
start = 0

while start < size:
    end = min(start + window_size, size)
    frame_to_send = frames[start:end]
    c.send(str(frame_to_send).encode())
    
    ack = c.recv(1024).decode()
    if ack:
        print(ack)
    
    start += window_size

c.close()
```
### Server:
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    received_data = s.recv(1024).decode()
    
    if not received_data:
        break

    print("Received frames:", received_data)
    s.send("Acknowledgement received from the server".encode())

s.close()
```
### PROGRAM:
![Screenshot 2024-03-10 191608](https://github.com/SHREELEKHAS/2b_SLIDING_WINDOW_PROTOCOL/assets/149768910/252f1970-7a97-469c-8b6b-8cda6e4fd069)

## OUPUT:
![Screenshot 2024-03-10 191718](https://github.com/SHREELEKHAS/2b_SLIDING_WINDOW_PROTOCOL/assets/149768910/b7d1149a-44d8-4828-8afb-f6ace689f85a)

## RESULT:
Thus, python program to perform implementation of sliding window protocol was successfully executed
