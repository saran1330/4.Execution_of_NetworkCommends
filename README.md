# 4.Execution_of_NetworkCommands
## AIM :Use of Network commands in Real Time environment
## Software : Command Prompt And Network Protocol Analyzer
## Procedure: To do this EXPERIMENT- follows these steps:
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
#PROGRAM
SERVER:
```
import socket
from pythonping import ping

# Create socket
s = socket.socket()

# Bind host and port
s.bind(('localhost', 8000))

# Listen for client connection
s.listen(1)

print("Waiting for connection...")

# Accept connection
c, addr = s.accept()
print("Connected to:", addr)

while True:
    # Receive hostname/IP from client
    hostname = c.recv(1024).decode()

    # Stop if client disconnects
    if not hostname:
        break

    print("Pinging:", hostname)

    try:
        # Ping the hostname
        result = ping(hostname, count=2, verbose=False)

        # Send result back to client
        c.send(str(result).encode())

    except Exception:
        c.send("Host Not Found".encode())

# Close connection
c.close()
s.close()
```
CLIENT:
```
import socket

# Create socket
s = socket.socket()

# Connect to server
s.connect(('localhost', 8000))

print("Connected to Server")

while True:
    # Get website/IP from user
    ip = input("Enter website or IP to ping (or 'exit' to quit): ")

    # Exit condition
    if ip.lower() == 'exit':
        break

    # Send data to server
    s.send(ip.encode())

    # Receive response from server
    response = s.recv(4096).decode()

    print("\nPing Result:")
    print(response)

# Close socket
s.close()
```



## Output
<img width="1833" height="1015" alt="Screenshot 2026-05-27 082956" src="https://github.com/user-attachments/assets/f0211917-0245-4276-9d86-e39dda82e866" />


## Result
Thus Execution of Network commands Performed 
