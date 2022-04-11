# Mitnick-attack
COMP8677-2-R-2022W (Networking and Data Security) - Project

## Team:
Abhishek Mehta (https://github.com/Abhishe-k)
Ashish Patel (https://github.com/ashishPatel10)
Hardikkumar Makwana (https://github.com/hardik1410)


## References:
https://seedsecuritylabs.org/Labs_20.04/Networking/Mitnick_Attack/

## Steps to run the attack

- First setup the docker container
**docker-compose up**

- Switch on to X-terminal
•	su seed
•	cd
•	touch .rhosts
•	echo <server ip> > .rhosts
•	chmod 644 .rhosts

- Now on trusted-server 
•	su seed
•	rsh <x-terminal ip> date
You would be able to see the date of the x-terminal on server terminal

- Now on x-terminal ping the server or enter the arp command on it to enter the mac address on server (in root folder)
arp -s [Server’s IP] [Server’s MAC]

- Now the first step is to stop the server / syn flood attack
Once the server is down, go to the attacker and spoof the syn packet to the x-terminal 
Respond to the SYN+ACK packet
Send the rsh data packet having the command
Setup the backdoor having the echo command (check if it is in su seed)

Now for the spoof alert go to the x-terminal and run the spoof-alert script
Now go to the attacker terminal and run the spoof the script



