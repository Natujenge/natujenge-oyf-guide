## Part 1: Understaning Server, Service and Ports:
+ **Hardware and software elements of a server**:
    + Has CPU(s)
    + Has Memory
    + Has Storage 
    + Has I/O devices:
        + Has **Network Interface Card(s)** - servers are expected be connected to network(s) and have IP address(es).
            + A server connected to multiple networks using different NIC cards. 
            + A network interface can be physical or logical. 
            + One server can have multiple IP address e.g. **lo0** with IP address 127.0.0.1, **eth0** with IP address 192.168.100.87
        + May have a **Keyboard** 
        + May have a **Monitor** 
    + Runs an **Operating System (OS)** - Linux, macOS, Windows, etc.
        + **OS Components**: file, memory, process and I/O management. 
        + The heart of the OS is the **Kernel** 
    + A server **can run multiple processes** (OS processes):
        + A process can run in **background** or *foreground*
            + Foreground - under direct control of interactive user (mostly attached to a terminal). 
            + Background - no control of an interactive user (not attached to a terminal). 
            + A process are identified by **process id** or **PID**
        + **A Daemon or a Service**- a process that has the following properties:
            + *Runs in the background* - no direct interaction with a user. 
            + *Often started during bootup*
            + *Often used for events that may happen at any time* e.g. web server that handles incoming HTTP requests need to run at any time or even a database service that requires to be accessed at any time. 
        + **Services can be accesssed remotely** - in case a service needs to be accessed remotely, we use ports to identify the service e.g. 
            + **Web (HTTP)** server/service - 80
            + **MySQL** server/service - port 3306  
            + **FTP (file transfer protocol)** service - port 21
            + **Secure Shell** service - runs on port 22
            + **Telnet** service - port 23
            + **SMTP (send mail)** server/service  - port 25
            + Your own **custom service** running on port 16777.
            + **NOTE**:
                + A port is a **16 bit number**
                + Value range: **0 - 65353** (65354 values - 2 power 16)
                + 0 - 1023 - reserved for for common TCP/IP applications and are called **well known ports**  
        + Some services **do not need to be accesssed remotely** and **do not necessarily need a port**. 
            + **Firewall** service that can allows or rejects network requests. 
        + It possible for **one service to expose two ports** for various use:
            + Web/HTTP service normally expose two ports:
                + **Port 80** - HTTP (Insecure - to be discussed later)
                + **Port 443** - Secure HTTP (HTTPS) 
        + A **service** serves requests and is commonly referred as a **server**.
            + A server can be a **physical or virtual server** with hardward resources attached to it. 
                + A VM on AWS or any other cloud provider is a server. 
            + A server can be a **software that runs on a physical server** (also known as service).
                + A Web or HTTP Server 
                + An Email or SMTP Server
+ **Shell**:
    + A Shell is a program that takes in commands from the keyword and gives them to the Operating System (think of Kernel) to perform. This is a **command line interface (CLI)** and is an alternative to **graphical user interface (GUI)**. 
    + **Linux Shells**:
        + sh - UNIX or Bourne Shell 
        + bash - Born Again Shell 
        + csh - C shell 
        + ksh - Korn Shell 
        + zsh - Z Shell 
        + etc... 
    + **Why Shell**?
        + Most servers do not come with GUI unlike our PCs and Macs. 
        + It is an important program for all software engineers - you cannot ignore shell. 
    + **Which Shell** are you using on Linux or macOS?
        + echo $SHELL 
+ **Terminal**
    + It is a program called *terminal emulator*. It opens a window (GUI) that **allows you interract with the shell**.
    + There are many terminal emulators out there. Linux and macOS comes with a default **Terminal**. 
    + Development tools come with a Terminal e.g. VS Code. 
    + Users on Windows can download **PuTTy** - https://www.putty.org/.  
+ **Server Access/Login**:
    + **Local access** - visit the server room and use the server keyboard to enter login credentials (similar to local laptop access/login) - using a **GUI** or **Terminal**. 
    + **Remote access** (requires the server to be on a network) - requires a special program for remote login:
        + Requires a special service to run on the server for remote access e.g. 
            + **Telnet** -  a network protocol used to virtually access a computer.  Runs on port 23. Not secure (data transferred in plain text).
            + **Secure Shell (SSH)**  - a program to login into another computer over the network to execute commands in a remote machine. Runs on port 22. Secure (data is encrypted during transfer). 
        + You may need a client program to use SSH or Telnet e.g. you can download **PuTTy**  or your default **Terminal** program. 

+ **Login to a Remote Server**
    + A server comes with an IP address and you need user credentials to login; either username & password pair or username & private key pair. 
    + **Login using a Username and Password**
        + *ssh username@ip_address* <-- you will be require to provide a password 
        *e.g. ssh root@51.15.211.168*
    + **Login using a Username and a Private Key**
        + *ssh -i private_key username@ip_address* <-- you will not be required to enter a password 
        + *e.g. ssh -i scaleway.pem root@51.15.211.168*
