## Simple Python 3 Web Server Build

#### Introduction
A web server is a piece of software that resides on a physical server and responses to external software making connection calls via HTTP protocol.

### The Build

#### Python 3 Code
(Note: Python programming language evolution may render the following code obsolete in the future.)

Save the following code in a GitHub repository folder as webserver1.py

```
import socket

HOST, PORT = '', 8888

listen_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
listen_socket.setsockopt(socket.SOL_SOCKET, socket.SO_REUSEADDR, 1)
listen_socket.bind((HOST, PORT))
listen_socket.listen(1)
print(f'Serving HTTP on port {PORT} ...')
while True:
    client_connection, client_address = listen_socket.accept()
    request_data = client_connection.recv(1024)
    print(request_data.decode('utf-8'))

    http_response = b"""\
HTTP/1.1 200 OK

Hello, world!
"""
    client_connection.sendall(http_response)
    client_connection.close()
```

### Executing the Code

#### Step 1: Command Line Entry
Enter the following into the system command line:

```
$ python webserver1.py
Serving HTTP on port 8888 …
```

#### Step 2: Entering the URL in a Web Browser
Open a web browser and enter the following in the broswer's address bar:

```
http://localhost:8888/hello
```

Hit Enter and the web browser shoudl display the text
```
Hello, world!
```
