SSH TUNNELING AND COVERT CHANNELS 

TUNNELING:
    |--> ENCAPSULATAION OF PROTOCOLS INSIDE OF OTHER PROTOCOLS
          DIFF TYPES OF TUNNELING USED WITH IPV
            |--> IPv6 over IPv4
                  Dual Stack
                  6in4
                  6to4
                  4in6
                  Teredo
                  ISATAP


COVERT CHANNELS:
    |--> Using common and legitimate protocols to transfer data in illegitimate ways
          Utilizes computer system resources, mechanisms, or protocols
          Transmits information contrary to design intent
          Bypasses security, violates policies, leaks sensitive data


TYPES OF COVERT CHANNELS:
    |--> STORAGE:
            |--> PAYLOAD
                  HEADER
    |--> TIMING:

COMMON PROTOCOLS USED WITH CHANNELS:
1. ICMP
2. DNS
3. HTTP


DETECTION OF COVER CHANNELS:
    |--> HOST ANALYSIS:
            |--> #Requires knowledge of each applications expected behavior



  |--> NETWORK ANALYSIS:
          |--> #A good understanding of your network and the common network protocols being used is the key
                #Baselining of what is normal to detect what is abnormal





CHANNEL DETECTION OVER ICMP:
    |--> #ICMP works with one request and one reply answer
            |--> Type 8 code 0 request
                  Type 0 code 0 answer.

  |--> Check for:
          |--> Payload imbalance
                Request/responce imbalance
                Large payloads in response
                


CHANNEL DETECTION OVER DNS:
    |--> DNS is a request/response protocol
          1 request typically gets 1 response
          Payloads generally do no exceed 512 bytes
            |--> Check for:
                          Request/response imbalances
                          Unusual payloads
                          Burstiness or continuous use
           

CHANNEL DETECTION OVER HTTP:
    |--> Request/Response protocol to pull web content
          GET request may include .png, .exe, .(anything) files
          Can vary in sizes of payloads
          Typically "bursty" but not steady



Steganography:
    |--> #Hiding messages inside legitimate information objects
            |--> Injection
                  Substitution
                  Propagation




Steganography Injection:
    |--> Done by inserting message into the unused (whitespace) of the file, usually in a graphic


Steganography Substitution:
    |--> Done by inserting message into the insignificant portion of the file


Steganography Propagation:
    |--> Generates a new file entirely
          Needs special software to manipulate file
          
          

          

(SSH) SECURE SHELL:
    |--> Provides authentication, encryption, and integrity
          Allows remote terminal sessions
          Used for tunneling and port forwarding
          Proxy connections


KEYS:
  |--> User Key - Asymmetric public key used to identify the user to the server
        Host Key - Asymmetric public key used to identify the server to the user
        Session Key - Symmetric key created by the client and server to protect the session’s communication


LOCATION:
  |--> Client Configuration File (/etc/ssh/ssh_config)
        Server Configuration File (/etc/ssh/sshd_config)
        Known Hosts File (~/.ssh/known_hosts)




SSH PORT FORWADING:
    |--> Creates channels using SSH-CONN protocol
          Allows for tunneling of other services through SSH
          Provides insecure services encryption



SSH OPTIONS:
    |--> -L - Creates a port on the client mapped to a ip:port via the server
          -D - Creates a port on the client and sets up a SOCKS4 proxy tunnel where the target ip:port is specified dynamically
          -R - Creates the port on the server mapped to a ip:port via the client
          -NT - Do not execute a remote command and disable pseudo-tty 



LOCAL PORT FORWARDING: 
    |--> BOX@ ssh -p <optional alt port> <user>@<server ip> -L <local bind port>:<tgt ip>:<tgt port>
    
   _                    |----> P- <ALT PORT IS TO DESIGNATE FOR THE LOCAL PORT ON THE HOST BOX>
                        |
          |-------------------------------------------------------|  
          |                                                       |
          |                                                       |
        BOX@  ssh -L <local bind port>:<tgt ip>:<tgt port> -p <alt port> <user>@<server ip>





Internet_Host:
ssh student@172.16.1.15 -L 1122:localhost:22
or
ssh -L 1122:localhost:22 student@172.16.1.15

Internet_Host:
ssh student@localhost -p 1122 
Blue_DMZ_Host-1~$
# THIS CONNECTION IS MADE OVER SSH 





Local Port Forward to localhost of server:
    |--> ssh student@172.16.1.15 -L 1123:localhost:23
          ssh -L 1123:localhost:23 student@172.16.1.15

Internet_Host:
telnet localhost 1123
Blue_DMZ_Host-1~$
# THIS CONNECTION IS MADE OVER TELNET 



Internet_Host:
ssh student@172.16.1.15 -L 1180:localhost:80
or
ssh -L 1180:localhost:80 student@172.16.1.15

Internet_Host:
firefox http://localhost:1180
{Webpage of Blue_DMZ_Host-1}
# THIS CONNECTION I MADE OVER HTTP 
# WHEN WORKING OVER HTTP MORE BTETTER TO USETHE WGET COMMAND REATHER THAN WEBPAGE INFO BUT GET IT HOW YOU GET IT 



Local Port Forward to remote target via server
    |--> Internet_Host: ssh student@172.16.1.15 -L 2222:172.16.40.10:22
                        ssh -L 2222:172.16.40.10:22 student@172.16.1.15

Internet_Host:
ssh student@localhost -p 2222
Blue_INT_DMZ_Host-1~$
# THIS CONNECTION IS MADE OVER DYNAMICALLY ASSISNED PORT



Forward through Tunnel:
    |--> Internet_Host:
          ssh student@172.16.1.15 -L 2222:172.16.40.10:22
          ssh student@localhost -p 2222 -L 3323:172.16.82.106:23

          Internet_Host:
          telnet localhost 3323
          Blue_Host-1~$



DYNAMIC PORT FORWARDING:
    |--> ssh -D <port> -p <alt port> <user>@<server ip>
          Proxychains default port is 9050
          Creates a dynamic socks4 proxy that interacts alone, or with a previously established remote or local port forward
          #PROXYCHAIN ONLY FORWARDS NETWORK TRAFFIC

REMOTE PORT FORWARDING:
    |--> ssh -R <remote bind port>:<tgt ip>:<tgt port> -p <alt port> <user>@<server ip>
    
Blue_DMZ_Host-1:
ssh student@10.10.0.40 -R 4422:localhost:22
or
ssh -R 4422:localhost:22 student@10.10.0.40

Internet_Host:
ssh student@localhost -p 4422
Blue_DMZ_Host-1~$
#THIS COMMAND IS BEING RAN ON THE REMOTE SYSTEM AND IS CONNECTING BACK TO THE LOCAL SYSTEM WITH THE -R






