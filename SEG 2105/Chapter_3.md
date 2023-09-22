# Reusable Software

## Building on the Work and Experience of Others
- make your code as reuseable as possible
- try to use other programmers code as often as possible

### Types of Reusing
 - Reuse of expertise
	 - experienced SE engineers can save time because they already know the solution to many problems
 - Reuse of standard desisngs and algorithms
 - Reuse of libraries or powerful commands
 - Reuse of frameworks
 - Reuse of complete programs

## Why Developers Don't Like Making Reusable Packages
- Developing anything reusable doesn't directly benefit the current customer
- Managers tend to only reward / encourage those who contribute to the 'visible part' (ie. quality of what the customer gets)
- Reusable software is often made in a hurry, lowering the overall quality, thus developers tend to lose confidence

This creates a vicious cycle:
developers don't develop high-quality code, therefore nothing good can be reused. Since nothing good can be reused, developers spend longer making a program, which gives them less time to make reusable code.

### How to Break the Cycle
Both software engineers and managers need to recognize the following if they want to break the cycle:
- The cycle exists and costs money
- In order to save money in the long term, you need to invest in reusable code
- Developers should be rewarded for developing reusable code
- Attention to quality of reusable components is critical, so reusers can be confident in them
- Developing reusable components often simplifies the design
- Developing and reusing components improves reliability
	- the more its implemented, the more testing it gets

### Making it Possible to Find Reusable Components
Being able to find the components is as important as them existing. Therefore it's important for reusable code to be catalogged and documented.
The catalog must be:
- easy to search
- kept up to date
	- deprecate (drop) any unreliable / outdated code 

# Frameworks
A framework is reusable software which provides a generic solution to a general problem.
In general: *applications that do different but related things tend to have similar designs.*

Frameworks are incomplete:
- certain classes/methods are used by the framework (mandatory), but are not implemented (slots)
- Some of the functionality is optional (hooks)
- devs use *services* that the framework provides (API)

## Object Oriented Frameworks
An object oriented framework is composed of libraries of classes. The API is defined as the set of **all public methods** of the classes. There tends to be a lot of interefaces and abstract classes.
Examples:
- A framework for payroll management
- A framework for frequent buyer clubs
- A framework for university registration
- A framework for e-commerce websites

## Types of Frameworks

### Horizonal Frameworks 
Horizonal frameworks are more generic, and can have a lot of different features


### Vertical Frameworks
A vertical framework (application framework) offer fewer features, but are more specialized.

# Client-Server Architecture

### Server
A program which provides a service for other programs (computers) that connect to it

### Client
A program which access a server(s) to obtain services

## Examples of Client-Server systems:
- World wide web
- Email
- Cloud-based services (Google Drive)
- Communication systems
- Databases

## Thin-client vs. Fat-client Systems

### Thin-client Systems
- Client is made as small as possible, easy to download
- Most work is done by server

Examples:
- Banking apps
- web browsers


### Fat-client Systems
- Clients do as much work as possible
- Servers can handle a lot more clients

Examples:
- video games
- Computers given to employees / students

## Communcation Protocol
- messages clients send to a server form a *language*
	- the server has to be programmed to understand the langeuage
- The messages the server sends to the client also form a language
	- The client needs to be programmed to understand that language
- The two languages and the rules of the 'conversation' form the **protol**

## Tasks to Perform When Developing Client-Server Applications

1. Design the primary work being performed by clients and servers
2. Design how the work is distributed
3. Design the details of the messages sent by clients and servers
4. Design the mechanism for:
	1. Initializing
	2. Handling connections
	3. Sending and recieving messages
	4. Terminating

## Technology Needed for Client-Server Systems

### Internet Protocol (IP)
- Route messages from computer to computer
- Long messages are usually split into smaller pieces

### Transmission Control Protocol (TCP)
- Handles *connections* between computers
- Computers can exchange IP messages over the connection
- Ensures messages have been recieved

### IP Addresses

IP addresses can be private or public

- **IPv4:**  (0-255).(0-255).(0-255).(0-255) (32 bits)
ex:		10.10.36.9
- **IPv6:**  same as ipV4 but 128 bits



### Port Numbers
All port numbers between 0 - 65536
Split into three categories:
- Reserved (0-1024)
	- Already in use by another application
	- Reserved/unavailable at all times
	- examples:
		- 21 ftp
		- 22 ssh
		- 443 web secure
		- 80 web
- Dynamic (1025-4096)
	- ports you can use if its available
	- Application ports
	- examples:
		- sql 1433
- Ephemeral (4097+)
	- temporary ports used for IP communcations


# Client-Server Code in Java

## Establishing a Connection

- the `java.net` package allows you to create a TCP/IP connection between two applications
- Before a connection can be established, the server must *listen* to one of the ports
```java
ServerSocket serverSocket = new ServerSocket(port);
Socket clientSocket = serverSocket.accept();
```

For a client to connect to a server:
```java
Socket clientSocket = new Socket(host, port);
```


## Exchanging Information

Each program uses instances of `java.io.InputStream` and `java.io.OutputStream` to send and recieve information

Examples:
```java
OutputStream output = clientSocket.getOutputStream();
InputStream input = clientSocket.getInputStream();
```

### Sending and Receiving Messages

Without filters (raw bytes):
```java
output.write(msg);
msg = input.read();
```

With primitive types:
```java
output.writeDouble(msg);
msg = input.readDouble();
```

With custom Objects:
```java
output.writeObject(msg);
msg = input.readObject();
```
