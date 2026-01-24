Lab Environment
In this lab environment, you will have GUI access to a Kali machine. The target machine will be accessible at target.ine.local.

Objective: Use Metasploit and manual investigation techniques to capture the following flags:

Flag 1: Gain access to the MSSQLSERVER account on the target machine to retrieve the first flag.

Flag 2: Locate the second flag within the Windows configuration folder.

Flag 3: The third flag is also hidden within the system directory. Find it to uncover a hint for accessing the final flag.

Flag 4: Investigate the Administrator directory to find the fourth flag.

## Lets start with an Nmap Scan on target.ine.local

![img](1.png)

lets perform service version detection and default script scan on the open ports found

![img](2.png)
![img](3.png)

we found the version of mssql server running  , lets use msf to search for the corressponding module 

![img](4.png)

lets try the first exploit module 

![img](5.png)

![img](6.png) 

We successfully got the meterpreter shell 

Lets check the root directory

![img](7.png)

Lets visit windows system configuration folder

![img](8.png) 

![img](9.png)

our permission is denied , so try escalate our privilage 

command : getprivs --> to list the ways to escalte the privilage 

getsystem --> use those methods and get us the prvileged session

![img](10.png)

![img](11.png)

Now we got the highest privilage in the system now lets config folder

![img](12.png)

![img](13.png)

Now lets search for flag3 with the system32 folder 

![img](14.png)

/s --> for search inside the sub folders

/b --> dont print detailed information , show only file path 

![img](15.png)

lets visit adminstrator user folder to find the fourth flag 

![img](16.png)

![img](17.png)

Lets check the Desktop folder 

![img](18.png)

We successfully found all the four flags

-------------------------------------------------THE END----------------------------------------------

