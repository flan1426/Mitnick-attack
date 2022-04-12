# Mitnick-attack
COMP8677-2-R-2022W (Networking and Data Security) - Project

## Team:
Abhishek Mehta (https://github.com/Abhishe-k)
Ashish Patel (https://github.com/ashishPatel10)
Hardikkumar Makwana (https://github.com/hardik1410)


## References:
https://seedsecuritylabs.org/Labs_20.04/Networking/Mitnick_Attack/

## Steps to create the required environment for Mitnick Attack

1. Setting up docker environment and newtork
 * docker-compose down
 * docker-compose build
 * docker-compose up
 * dockps

2. Configure X-Terminal to allow free access by trusted-server
 * docksh container_id_of_XTerminal
 * su seed
 * cd
 * touch .rhosts
 * echo server_ip > .rhosts
 * chmod 644 .rhosts

3. On trusted-server, check if our configurations from step 2 work
 * su seed
 * rsh x-terminal_ip date
You would be able to see the date of the x-terminal on server terminal which means server can access X-terminal's remote shell without authentication

4. Now from x-terminal ping the server or register server ip and mac in arp cache (in root folder)
  * arp -s Server_IP Server_MAC
  Or
  * ping Server_IP
  * arp

5. Silent the server by stopping it or with syn flood attack

The above 5 steps creates the necessary condition that enabled Mitnick to perform his attack


## Steps to run the attack

1. From seed-attacker container, send a spoof packet with SYN message to the X-Terminal, wait and receive the SYN + ACK packet from X - terminal along with sending rsh data packet, and respond with ACK packet to X-terminal to perform a TCP handshake with X-Terminal ( Run spoof_session_syn.py )
2. After this, X-terminal will send a SYN packet to establish rsh session from it's side, receive the packet and send SYN + ACK message. (Run spoof-synack.py)
3. Implant a backdoor in X-terminal( Run backdoor.py)

After performing above 3 steps, attacker can gain access to X-Terminal's remote shell from any machine and do anything!

## Detection
1. Run the script spoof-detection.py on X-terminal
2. Repeat the attack using above steps.

You will find that the detection script will alert the X-Terminal system and print the message that it is been send spoof packects.
