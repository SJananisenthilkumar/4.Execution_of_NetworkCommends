# 4.Execution_of_NetworkCommands
## AIM :
Use of Network commands in Real Time environment
## Software : 
Command Prompt And Network Protocol Analyzer
## Procedure: 
To do this EXPERIMENT- follows these steps:
<BR>
In this EXPERIMENT- students have to understand basic networking commands e.g cpdump, netstat, ifconfig, nslookup ,traceroute and also Capture ping and traceroute PDUs using a network protocol analyzer 
<BR>
All commands related to Network configuration which includes how to switch to privilege mode
<BR>
and normal mode and how to configure router interface and how to save this configuration to
<BR>
flash memory or permanent memory.
<BR>
This commands includes
<BR>
• Configuring the Router commands
<BR>
• General Commands to configure network
<BR>
• Privileged Mode commands of a router 
<BR>
• Router Processes & Statistics
<BR>
• IP Commands
<BR>
• Other IP Commands e.g. show ip route etc.
<BR>
## Program
Client :
```
import socket
from pythonping import ping
s=socket.socket()
s.bind(('localhost',8000))
s.listen(5)
while True:
   c,addr=s.accept()
   print("Connection from",addr)
   try:
      hostname=c.recv(1024).decode().strip()
      if hostname:
         try:
            response=str(ping(hostname,verbose=False))
            c.send(response.encode())
         except Exception as e:
            c.send("Ping failed: {}".format(e).encode())
      else:
               c.send("Hostname not provided".encode())
   except Exception as e:
     print("Error:",e)
   finally:
     c.close() 
#s.close()
```
Server :
```
import socket
s=socket.socket()
s.connect(('localhost',8000))
try:
   while True:
      ip=input("Enter the website you want ti Ping:")
      s.send(ip.encode())
      response=s.recv(1024).decode()
      if response:
         print("Ping Result:",response)
      else:
         print("No response frm server.")
except Exception as e:
   print("Error:",e)
finally:
   s.close()
```
## Output
Client & Server :

![image](https://github.com/SJananisenthilkumar/4.Execution_of_NetworkCommends/assets/144871139/d2ae14cc-6e33-4ac8-86ff-ef7f8c5f8a95)

Traceroute Command :

![image](https://github.com/SJananisenthilkumar/4.Execution_of_NetworkCommends/assets/144871139/9eb20b5e-42dc-4f5c-9e88-00a4be9fd1e6)


## Result
Thus Execution of Network commands Performed 
