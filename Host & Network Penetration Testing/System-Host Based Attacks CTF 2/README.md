In this lab environment, you will be provided with GUI access to a Kali Linux machine. Two machines are accessible at http://target1.ine.local and http://target2.ine.local.

Objective: Perform system/host-based attacks on the target and capture all the flags hidden within the environment.

Flags to Capture:

Flag 1: Check the root ('/') directory for a file that might hold the key to the first flag on target1.ine.local.

Flag 2: In the server's root directory, there might be something hidden. Explore '/opt/apache/htdocs/' carefully to find the next flag on target1.ine.local.

Flag 3: Investigate the user's home directory and consider using 'libssh_auth_bypass' to uncover the flag on target2.ine.local.

Flag 4: The most restricted areas often hold the most valuable secrets. Look into the '/root' directory to find the hidden flag on target2.ine.local.

## Lets start with an Nmap Scan on target1.ine.local

![img](1.png) 

lets perform service detection scan and default script scan on port 80

![img](2.png)

lets visit the site 

![img](3.png)

We can notice that it runs a cgi runs 

CGI = Common Gateway Interface

CGI is a standard interface that allows a web server (like Apache) to run external programs or scripts and send their output back to a web browser.

Shellshock is a vulnerability in Bash where Bash executes commands hidden inside environment variables.

lets use msf check whethere the cgi is vulnerable or not

![img](4.png)

![img](5.png)

seems it is vulnerable so lets exploit it 

![img](6.png)

![img](7.png)

![img](8.png)

we successfully got the meterpreter session 

![img](9.png)

![img](10.png)

We suceessfully found the flag1 and flag2 

## Lets start with an Nmap scan on target2.ine.local

![img](11.png)

only ssh is open , lets perform service verison detection and default scan on it 

![img](12.png)

we found a ssh service , lets use msf to search for the module 

![img](13.png)

![img](14.png)

![img](15.png)

we got a session created , lets interact with it 

![img](16.png)

now lets escalate our privilage to read the flag4 ,

searching fot suid files where /user/welcome sounds intersting 

![img](17.png)

lets analyze it 

![img](18.png)

seems like welcome is executes the file greetings when it is run 

so lets remove the greetings like , since we cant able to edit or modify it and create a new greetings file with /bin/bash file contents 

![img](19.png)

![img](20.png)

![img](21.png)

We have successfully found the flag3 and flag4 

--------------------------------------------------------------------------------------------




