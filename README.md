# 2a_Stop_and_Wait_Protocol
## AIM 
To write a python program to perform stop and wait protocol
## ALGORITHM
1. Start the program.
2. Get the frame size from the user
3. To create the frame based on the user request.
4. To send frames to server from the client side.
5. If your frames reach the server it will send ACK signal to client
6. Stop the Program
## PROGRAM
### sever side:
```
import socket
server_socket = socket.socket()
server_socket.bind(('localhost', 12345))
server_socket.listen(1)
print("Server is waiting for connection...")
conn, addr = server_socket.accept()
print("Connected to client:", addr)
while True:
    frame = conn.recv(1024).decode()
    if frame == "exit":
        print("Transmission completed.")
        break
    print("Received frame:", frame)
    ack = "ACK"
    conn.send(ack.encode())
conn.close()
server_socket.close()
```

 client side:
```
import socket
import time
client_socket = socket.socket()
client_socket.connect(('localhost', 12345))
n = int(input("Enter number of frames to send: "))
for i in range(1, n + 1):
    frame = f"Frame {i}"
    print("Sending:", frame)
    client_socket.send(frame.encode())
    ack = client_socket.recv(1024).decode()
    print("Received:", ack)
    time.sleep(1)

client_socket.send("exit".encode())
client_socket.close()
```

## OUTPUT
### sever side
<img width="1919" height="985" alt="image" src="https://github.com/user-attachments/assets/8897d813-de0d-43a9-8287-443e6efa35bf" />
### client
<img width="1917" height="1034" alt="image" src="https://github.com/user-attachments/assets/7237eb51-a767-44d8-a217-2d4d39b76deb" />

## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
