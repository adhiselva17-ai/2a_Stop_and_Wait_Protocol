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
receiver.py
```
import socket

s = socket.socket()
s.bind(('localhost', 8000))
s.listen(1)

print("Waiting for server...")
c, addr = s.accept()

n = int(input("Enter number of frames: "))

for i in range(n):
    data = input("Enter frame: ")

    c.send(data.encode())

    ack = c.recv(1024).decode()
    print("Server:", ack)

c.close()
s.close()
```
sender.py
```
import socket

s = socket.socket()
s.connect(('localhost', 8000))

while True:
    data = s.recv(1024).decode()

    if not data:
        break

    print("Received Frame:", data)

    s.send("ACK Received".encode())

s.close()

```
## OUTPUT
<img width="565" height="285" alt="Screenshot 2026-11-03 094114" src="https://github.com/user-attachments/assets/b3ae034b-b19a-47b9-bcc4-08c420a51b88" />
<img width="581" height="135" alt="Screenshot 2026-11-03 094039" src="https://github.com/user-attachments/assets/2fcf868f-3568-4094-96d2-e34ac75a7149" />


## RESULT
Thus, python program to perform stop and wait protocol was successfully executed.
