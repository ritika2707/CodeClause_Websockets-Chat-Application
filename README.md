# Websockets-Chat-Application
## How to run the project
Clone this repo in vs code by opening new window using Ctrl+shift+N and then selecting the option clone github rep then search for ritika2707/CodeClauseWebsocketsChatApplication
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
