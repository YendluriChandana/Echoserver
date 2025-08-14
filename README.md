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
HOST = '127.0.0.1' 
PORT = 65432 
with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.bind((HOST, PORT))
    s.listen()
    print(f"Server started. Listening on {HOST}:{PORT}...")
    conn, addr = s.accept()
    with conn:
        print(f"Connected by {addr}")
        while True:
            data = conn.recv(1024)
            if not data:
                break
            conn.sendall(data)
```
client.py
```
import socket


HOST = "127.0.0.1"  # The server's hostname or IP address
PORT = 65432  # The port used by the server


with socket.socket(socket.AF_INET, socket.SOCK_STREAM) as s:
    s.connect((HOST, PORT))
    s.sendall(b"Hello, world")
    data = s.recv(1024)


print(f"Received {data!r}")


      
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
![WhatsApp Image 2025-08-14 at 08 20 39_2404d095](https://github.com/user-attachments/assets/a0a167a8-13f8-45f0-8dfc-de3f57af1ea2)

### SERVER OUTPUT:
![WhatsApp Image 2025-08-14 at 08 20 09_3be37ba3](https://github.com/user-attachments/assets/772620bf-a2d9-4d2b-8b2e-d10be1dc59c8)

## RESULT:
The program is executed succesfully
