# Multithreaded-Chat-Application
It's a console-based multithreaded ChatServer that employs Java Socket programming. Sockets are used to communicate between client and server. Server actively listens for connection requests from clients across the network. Clientside socket connect to the server via an IP address and port number. In our case server is listening on localhost and port:1234. The client selects his or her username in the chat room after connecting to the server. The client submits a message, which is then transmitted to the server using Java's OutputStreamWriter and the server reads the message using Java's InputStreamReader in the simiilar way server broadcast this message to the other clients.
## How to run the project
Clone this repo in vs code by opening new window using Ctrl+shift+N and then selecting the option clone github rep then search for saranshgour5/MultithreadedChatApplication
it'll clone all the files into your computer. then first server.java and then run multiple times client.java and enter username for each client.
## Working of the project
This project consists of three classes Server.java, ClientHandler.java, Client.java.<br/>
Let's discuss working of each one by one.<br/>
### Server.java
In this class we are setting up our server which is actively accepting the socket connection from clients on port:1234 and in this class we create a object from ClientHandler class which is responsible for communicating between the client and server. ClientHandler class implements runnable interface. Runnable is an interface that is to be implemented by a class whose instances are intended to be executed by a thread. and if any IOexception occur we close the server.
### ClientHandler.java
This class is responsible for communicating with client. The work of this class is to listen the messages from the clients and broadcasting it to the other clients on the server. We maintain a arrayList for clients whenever a new clients comeup we add his credentials in the arraylist. I have used mutex lock for this part of the code to prevent race condtion. Now Listening for the messages is executed by a seprate thread because it's a blocking operation and there is other part of code which is independent from this operation like reading the message. To broadcast the message recieved from client we have maintained an Arraylist we use buffered writer to send the message. If the client disconnects from the server we remove the client from arrayList.
### Client.java
The functionality of this is very similar to the ClientHandler.java instead of server listening the message and broadcasting the meassage, here client listen message from the server and send message to the server. We create a socket to connect to the server. Everytime a new client comes up we ask his/her username and use InputStream and OutputStream for transferring the messages.
## Your learning from the project
1. How the processors execute it's processes
2. Working of threads
3. Multithreading in java
4. How the server and client communicates 
5. Socket programming 
## A short video demo 
https://drive.google.com/file/d/1_OUBBgstGcjRm7CuPBV-9xOiW3ZEvlcx/view?usp=sharing
## Resources/references used 
<a href="https://drive.google.com/drive/folders/1056_HjCW0tRu_t6VeM7r6A2bkkKXM2C5" target="_blank">ACM IITR video lectures</a><br/>
<a href="https://github.com/acmiitr/Multithreaded-Server" target="_blank">ACM IITR demo Multithreaded Server</a><br/>
https://www.javatpoint.com/socket-programming



