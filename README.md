# Echoserver
Echo server and client using python socket
# AIM:

To develop a simple webserver to serve html programming pages.

## DESIGN STEPS:

### Step 1:

HTML content creation is done

### Step 2:

Design of webserver workflow

### Step 3:

Implementation using Python code

### Step 4:

Serving the HTML pages.

### Step 5:

Testing the webserver

## PROGRAM:
server.py
```
import socket

# Create a TCP/IP socket
server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Bind the socket to an address and port
server_socket.bind(('localhost', 12345))
server_socket.listen(1)

print("Server is listening on port 12345...")

# Wait for a connection
conn, addr = server_socket.accept()
print(f"Connected by {addr}")

while True:
    data = conn.recv(1024)
    if not data:  # If no data, client closed connection
        break
    print(f"Received from client: {data.decode()}")
    conn.sendall(data)  # Echo back the same data

conn.close()

```
client.py
```
import socket

# Create a TCP/IP socket
client_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)

# Connect to the server
client_socket.connect(('localhost', 12345))

while True:
    msg = input("Enter message (type 'exit' to quit): ")
    if msg.lower() == 'exit':
        break
    client_socket.sendall(msg.encode())
    data = client_socket.recv(1024)
    print(f"Echo from server: {data.decode()}")

client_socket.close()
      
```
##  Architecture Diagram

```bash
+--------------------------+
|  User's Web Browser      |
|  (Client: Chrome/Firefox)|
+-----------+--------------+
            |
            |  HTTP Request (GET /)
            v
+-----------+--------------+
|   Python Web Server      |
| (http.server + Handler)  |
| - Listens on Port 8000   |
| - Handles GET Requests   |
| - Sends HTML Response    |
+-----------+--------------+
            |
            |  HTML Response
            v
+--------------------------+
|  User Sees Rendered Page |
|  <h1>Hello Web Server</h1>|
+--------------------------+
```


## OUTPUT:
### CLIENT OUTPUT:
<img width="825" height="417" alt="Screenshot 2025-08-14 084829" src="https://github.com/user-attachments/assets/933b1134-7c52-4e8d-b567-9ff5bcc146c7" />


### SERVER OUTPUT:
<img width="814" height="228" alt="Screenshot 2025-08-14 085258" src="https://github.com/user-attachments/assets/6830e104-1600-429a-b720-1a3b739dc8a9" />



## RESULT:
The program is executed succesfully
