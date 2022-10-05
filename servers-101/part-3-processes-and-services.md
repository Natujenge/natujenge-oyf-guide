
# Recap of Servers 101 Part 1 and 2 

+ Recap of server 1 session:
    + Server is **comprised of hardware resources and has an OS**
    + Server can **have multiple IPs addresses**:
        + localhost/127.0.0.1
        + 10.1.100.7 - server LAN IP 
    + A server can **run multiple services**:
        + sshd - ssh service/daemon/server 
        + httpd - http/web service/daemon/server
        + mysqld - MySQL service/deamon/server 
    + A **service can expose port(s)** in the range of 0-65353 [0-1023 reserved for well known services]
    + A service can expose port(s) for access via network: 
        + **web service (httpd)** - exposes 80 and 443 - a well known service 
        + **ssh service (ssh)** - exposes 22 - well known port 
        + **mysql service (mysql)** - exposes port 3306 - NOT a well known port 
        + **your-app** - exposes a port 8080 - NOT a well known port 

# Part 3: Process & Service Management 

## Service Management 
+ We will dive deeper into management of services in CentosOS Stream/RHEL (other Linux distros will use different commands and service names may vary - but the concepts hold)
    + **install** 
        + yum install <service_name>
        +e.g. _yum install httpd_
    + **start**
        + systemctl start <service_name>.service
        + old: service <service_name> start 
        + e.g. _systemctl start httpd.service_

    + **stop** 
        + systemctl stop <service_name>.service
        + old: service <service_name> stop 
        + e.g. _systemctl stop httpd.service_

    + **restart** 
        + systemctl restart <service_name>.service
        + old: service <service_name> restart 
        + e.g. _systemctl restart httpd.service_

    + **check status** 
        + systemctl status <service_name>.service
        + old: service <service_name> status 
        + e.g. _systemctl status httpd.service_

+ In most cases a **service is made up of** the following:
    + **Binary files** - normally under /usr/sbin folder 
        + e.g. /usr/sbin/httpd
    + **Configuration files** - normally under **/etc** folder
        + e.g. _/etc/httpd_ folder and a main configuration file _/etc/httpd/conf/httpd.conf_ 
    + **Run files** - normally under **/run** folder 
        + e.g. _/run/httpd/_ folder and _/run/httpd/http.pid_
    + **Data path** - where the main application data is stored. Dependent on the application:
        + e.g. _/var/www/html_ document root for Apache web server. All web pages are hosted here.
    + **Service ports:**
        + e.g. **80** for httpd service 

+ **Challenge:** Install **mysql service** as a group and study what comprises mysql service. 

**Process Management**
+ **Recap** Redirecting Output 
    + **cat** command to print the content  :
        [root@natujenge-oyf kamochu]# cat file1.txt_
        _Test content line 1
        Line 2
    + **wc** command to count the lines/words/characters 
        [root@natujenge-oyf kamochu]# wc file1.txt 
        2  6 27 file1.txt
    + **redirecting** output or pipelining 
        + e.g. _cat file1.txt | wc -l_

        + e.g. _echo "Hello World" | wc -c_

        + e.g. _echo "Hello World" | wc -w_

+ **Common Commands**:
    + A few commands that can help you in running process: 
        + **ps** command - Process Status command  
            + prints all currently running processes and their **pids**
            + Reads process information from virtual files in **/proc** file system 

            + Some usage examples:
                + ps 
                + ps -ef 
                + ps -ef | grep httpd

            + Ref: https://www.geeksforgeeks.org/ps-command-in-linux-with-examples/ or **man ps** 

        + **kill** command 
            + terminate process manually 
            + kill commands sends a signal to a process which terminates the process 

            + killing the parent process kills the child

            + Some usage examples:
                + kill _pid_
                + kill -l 
                + kill -9 _pid_ 

            + Ref: https://www.geeksforgeeks.org/kill-command-in-linux-with-examples/ or **man kill**


## Service Ports  

+ We need to learn a few commands that can be used in checking ports: 
    + Checking if a port is being used or open:
        + **netstat command**  - checking open ports 
            + _netstat -an | grep 80_ - checks if port 80 is being used  
        + **telnet command**
            + _telnet ip_address port_ - checks if the port is open on the server (whether the server is listening for connections)
                + e.g. telnet 127.0.0.1 80 
                + the command actually initiates a connection request (a TCP handshake)

    + Checking a server is responding to a request:
            + **telnet command** - see above 

    
## [Docker] Service Ports in the Context of Containers 
+ Containers are **actually processes** running on the host machine (with some good isolation). 
+ Containers running on a host server belong to a network (by default **bridge** network). 
    + Each container is assigned an IP address e.g. 172.17.0.2
    + Command:
        + _docker inspect [container_id|container_name]_ 
    + This implies that **a service inside a container can be expose a port** for access via the network:
        + The port ranges apply 0 - 65353 
        + Unique way of accessing the service is:
            + **conatiner_ip_address:service_port** e.g. 172.17.0.4:3306 
    + **Challenge:**
        + Bridge network is only accessible inside the host computer.
        + How do we then allow the rest of the world to access the service inside a container (e.g. access our website)?
            +  **Solution: Port Mapping**
                + Map the port inside the container to a port on the host machine 
                    e.g. **-p host_machine_port:container_port** 


## Containerization vs Virtualization

You can do some reading here:

+ ttps://medium.com/@krishankdwivedi/containerization-and-virtualization-7ac59b788268
+ https://www.redhat.com/en/topics/virtualization/what-is-a-hypervisor

## Today's Challenge

+ **Task 1:** Set up your webapp on the apache folder on the host VM: 
    + cd /var/www/html/
    + mkdir groupX - where X is your number 

+ **Task 2:** Setup a containerized MySQL DB Service 
    + Every group to run a MySQL database container with the following configurations:
        + container-name: mysql-grpX - where X is your group number 
        + port mapping:
            + MySQL exposes port 3306 
            + You will need to map port 3306 to a port on host machine using below rules:
                + 33<group_no_in_2_digits> e.g. 3301 for group 1, 3311 for group 11
    
    + Login to your DB service and do the following:
        + Create database - you can give it your own name 
        + Create a table - think of a table to be created 
        + Insert some data into the table
        + Play with SQL statements (query, update, etc)


# References:

+ Powerpoint presentation: https://docs.google.com/presentation/d/19Ji21DN9yrpz-FT_gNXUXXlS12tkcqIOJEKM_t6OTmQ/edit?usp=sharing
