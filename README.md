# Challenge MAchien FCBarcelona 

## Intro : 
machine : a VM deployed locally 
# Recon 
nmap 
'''shell 
cat result 
'''
## open ports 
 
80 : web port : gobuster , nothing special 

nothing to find here :( :( 
 
445 : open  netbios-ssn Samba 445/tcp open  microsoft-ds   139:  open  netbios-ssn

nothing worked here , even we try the metasploit 

21 : FTP port 

here let's try to connect over FTP 
''shell
ftp ipaddress
'''
default login 
anonymous 
and bow it's work 

let's see what we can do 
'''shell
ls
get notice.txt
'''
here we found a file named notice.txt 
let's what's inside : 

hi, as you know, this box is about brute force, as the suggestion says. As long as you don't get to root, keep guessing and applying brute force and brute force. Let's say for example, in our web application we like to keep things under a staduim that we love so much in Barcelona. well you have the list of staduims try to find what you are looking for;)
en spanish language but we translated it with Google hahahah h 


so the content of this file tell us to bruteforce the login with ssh connection 



22 : ssh port 

how how let's try bruteforcing the login with the stadium list 

tool we can bruteforce with : 
### hydra or graphic hydra 
### 