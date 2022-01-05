# PortScanner_for_begginers-
A simple PortScanner for mid-level educated students in python.If you are begginer you will not understand some functions but the comments i believe gonna help!!!!😂😂😂

#This is the code of our programme
#CODE#
#If you are in linux or mac try this at begin: /bin/python3
#############
import sys
import socket
from datetime import datetime
#Specifyin our target
if len(sys.argv) == 2:
	target = socket.gethostbyname(sys.argv[1])#We are translate host name to the IPv4 address(IP)
else:
 	print("Invalid amount of arguments❌")	
 	print("Syntax: python3 Got_Scann.py <ip>")
#Make our programm  aesthetic of course
print("--" * 25)
print("⏳⏳" * 25)
print("Scanning target "+target)
print("Time started"+str(datetime.now()))
print("⏳⏳" * 25)
print("--" * 25)
#Now the basic programm|results|errors
try: 
	for port in range(50,300):  #Port range isn't neccesary be the same bcs th amount of ports in networking is 65,535 so wetry manage and more specific our scan
		s = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
		result = s.connect_ex((target,port)) # returns an error indicator
		if result == 0:
			print("Port !!! {} !!! is open".format(port))
		s.close()
except KeyboardInterrupt:  #e.x. CTRL+C or ALT+F4
	print("\nExiting Program.")
	sys.exit()
except socket.gainerror:   #e.x.  wrong host name like ''
	print("Hostname couldn't be resolved.")
	sys.exit()
except socket.error:	#e.x. troubleshot from network or a server 
	print("Sorry we couldn't connect to server.😥😥😥")
	sys.exit()
##################

