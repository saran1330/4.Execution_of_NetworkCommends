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

## program
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
<img width="1090" height="315" alt="Screenshot 2026-05-20 081929" src="https://github.com/user-attachments/assets/3cc3557f-c822-49bf-8d7b-264244d4d19f" />

NETSTAT:
<img width="1101" height="1017" alt="Screenshot 2026-05-20 090358" src="https://github.com/user-attachments/assets/a1c66064-5d84-47bd-aa4d-5619e346a88a" />
IPCONFIG:
<img width="1086" height="752" alt="Screenshot 2026-05-20 090449" src="https://github.com/user-attachments/assets/d2eea2c0-07d8-461e-832a-c9d0f5b3f02a" />
PING:
<img width="1092" height="427" alt="Screenshot 2026-05-20 090536" src="https://github.com/user-attachments/assets/b019b2de-463d-4533-9d74-e296a2cf5ad9" />
TRACERT:
<img width="1082" height="557" alt="Screenshot 2026-05-20 090702" src="https://github.com/user-attachments/assets/82890372-fc34-4e96-86f3-1bde9edf63ae" />
NSLOOKUP:
<img width="1082" height="577" alt="Screenshot 2026-05-20 090835" src="https://github.com/user-attachments/assets/d29f36a0-e520-44f4-9319-d91d52aff257" />
GETMAC:
<img width="1106" height="340" alt="Screenshot 2026-05-20 090923" src="https://github.com/user-attachments/assets/ec717bff-d253-41dc-9f1e-6050af3b4396" />
HOSTNAME:
<img width="1095" height="220" alt="Screenshot 2026-05-20 090954" src="https://github.com/user-attachments/assets/b51c6418-9054-4f9c-af42-2501773f704b" />
NBTSTAT:
<img width="1113" height="767" alt="Screenshot 2026-05-20 091026" src="https://github.com/user-attachments/assets/6f2ad6a7-8b61-44b2-bd7b-0dffc27cf188" />
ARP:
<img width="1095" height="840" alt="Screenshot 2026-05-20 091119" src="https://github.com/user-attachments/assets/e0722ebc-edd8-4bdb-a93a-51d61c874628" />
SYSTEMINFO:

<img width="687" height="972" alt="Screenshot 2026-05-20 091222" src="https://github.com/user-attachments/assets/65622aa1-79fc-4331-825b-e2e41fcfc31d" />

## Result
Thus Execution of Network commands Performed 
