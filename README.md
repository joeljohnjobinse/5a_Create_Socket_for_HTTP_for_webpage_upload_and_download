# 5a_Create_Socket_for_HTTP_for_webpage_upload_and_download
## AIM :
To write a PYTHON program for socket for HTTP for web page upload and download
## Algorithm

1.Start the program.
<BR>
2.Get the frame size from the user
<BR>
3.To create the frame based on the user request.
<BR>
4.To send frames to server from the client side.
<BR>
5.If your frames reach the server it will send ACK signal to client otherwise it will send NACK signal to client.
<BR>
6.Stop the program
<BR>
## Program 
```
import socket

def handle_request(request):
    response = "HTTP/1.1 200 OK\nContent-Type: text/html\n\n<h1>Hello, World!</h1>"
    return response

def main():
    host = ''
    port = 8080

    server_socket = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    server_socket.bind((host, port))
    server_socket.listen(5)

    print("HTTP server listening on port", port)

    while True:
        client_socket, client_address = server_socket.accept()
        print("Client connected:", client_address)

        request_data = client_socket.recv(1024).decode()
        print("Received request:\n", request_data)

        response = handle_request(request_data)
        client_socket.sendall(response.encode())

        client_socket.close()

if __name__ == "__main__":
    main()
```
## OUTPUT
![image](https://github.com/user-attachments/assets/c1eeda46-8cd6-44e5-8a3b-f8e96666fb14)

## Result
Thus the socket for HTTP for web page upload and download created and Executed
