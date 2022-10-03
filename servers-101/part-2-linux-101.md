## Part 2: Linux 101 

### Part 2.1: What is Linux?

Linux is an Operating System's kernel that is based on UNIX. In enterprise software engineering, you cannot ignore Linux. 

Most large enterprises here in Kenya use **Redhat Enterprise Linux** (RHEL - enterprise grade Linux distribution with commercial support) as their OS. We will be using **CentOS** (a free and community supported Linux distribution). 

## Part 2.2: Most Common Linux Commands 

Note: Most commands come with **optional parameters** or **switches** that you can pass (e.g. **ls -a** or **ls --all** or **mysql --host=127.0.0.1 --port=3306 -uroot -ppassword** )

Note: **Standard streams** -  
    + stdin - standard input 
    + stdout - standard output 
    + stderr - standard error 

+ **ssh** - secure shell and used for remote login. 
+ **ls** - directory listing (windows equivalent is *dir*). 
    + **hidden files** and directories begin a . e.g. **.gitignore** file  or **.git/** directory 
        + use **-a** or **--all** switch to display all files including hidden files. 
+ **pwd** - print working directory - prints current directory. Talking of directory:
    + . - current directory 
    + .. - parent directory 
    + ~ - home directory 
+ **cd** - change directory 
+ **cp** - copy a file or directory 
    + _cp /path/to/source/file /path/to/destination/_
+ **cat** - reads the file and prints on standard output (used to view the content of file) 
    + do not cat binary files - use it on text based files 
    + can be used to create new files or append content to existing files:
        + **cat > hello.txt**  - creates or overwrites
        + **cat >> hello.txt** - creates or appends
+ **scp** - secure copy protocol - copy files from one directory to another (I use it when transferring files from my local directory to a remote directory)
    + e.g. _scp /path/to/file.txt user@hostname:/path/to/destinatio/_
    + e.g. _scp user@hostname:/path/to/source/file.txt /path/to/local/destination/
+ **mv** - move or rename a file 
    + _mv oldfilename newfilename_
    + _mv /path/to/current/file /path/to/destination_
+ **clear** - clear screen
+ **rm** - delete file or directory (with additional switches)
    + _rm filename_
    + _rm -rf folder/with/files/_
+ **grep** - search for a string in a file 
    + key in operations 
+ **tail** - prints the last lines in a file to standard output 
    + key in operations 
+ **head** - prints the first lines in a file to standard output 
    + key in operations 
+ **tcpdump** - used to capture network trace 
    + very useful in troubleshooting complex integrations 
+ **netstat** - net stats 
+ **history** - show previous comamnds 
    + **!** - can be used to run commands from history
+ **man** - help or manual command 
    + _man ls_ - manual for ls command 
+ **date** - displays the date and time 
+ **mkdir** - create a new directory or folder 
+ **echo** - to print something on the standard console 
+ **vim** - file editor 
+ **exit** - leave the terminal or command window 
+ **ps** - display running tasks/processes 
+ **kill** - to kill a process or task 
+ **traceroute** - print route packets trace to network host 
+ **cron and crontab** - scheduling tasks to be run the by OS. 
+ **ping** - to send ICMP echo request to a network host 
+ **sudo** - superuser do - lets you act as a super user or root user while you're a specific command

+ **alias and unalias** 
+ **chmod** - change the mode (permissions) of a file 
+ **top** 
+ **apt yum** 
+ **psswd** - change password 
+ **which** - outputs the full path of the shell command 
+ **less** -  inspect files backward and forward (related to tail)
+ **wc** - word count command and returns the number of words in a text file 
+ **uname** 
+ **find** 
+ **sed** 
+ **wget** 
+ 


## Part 2.3: Chaining Commads

Chaining commands in Linux allows us to execute multiple commands at the same time and directly through the terminal.


Read more: https://www.geeksforgeeks.org/chaining-commands-in-linux/

## Part 2.4: Redirecting Standard Input & Output

+ **Input Redirection** (< and <<)
    + Data comes from another source instead of standard input 
        + command < infile 
+ **Output Redirection** (> and  >>)
    + Data is redirected from standard output to another output stream
+ **Piping** (|)
    + Data from one command is sent to another command 


## Part 2.4: Recommended Future Work 
+ Shell Scripting 
    + **./** command
+ Crontab 
+ AWK Scripting 










## References 
+ https://linuxcommand.org/lc3_lts0010.php
+ https://www.digitalocean.com/community/tutorials/different-types-of-shells-in-linux
+ https://www.geeksforgeeks.org/linux-vs-windows-commands/
+ https://maker.pro/linux/tutorial/basic-linux-commands-for-beginners
+ https://kinsta.com/blog/linux-commands/
+ https://www.techtarget.com/searchnetworking/definition/Telnet
+ https://www.putty.org/
+ https://www.quora.com/What-are-the-fundamental-differences-between-a-process-and-a-service
+ https://www.puttygen.com/windows-terminal-emulators
+ https://en.wikipedia.org/wiki/Standard_streams



## Additional notes: 

+ Ask about people who have sent a HTTP request  
    + Browser 
    + Curl 
    + Wget 
    + Postman 
    + Telnet?? This is now a new one.... 
+ Use this session to set stage:
    + MySQL installation and 101 using the 7 questions (https://meliora.co.ke/articles/dfc1312e)
    + Web Server Installation and 101 using the 7 questions model. 
    + Docker installation and 101 using the 7 qestion model. 
+ 
