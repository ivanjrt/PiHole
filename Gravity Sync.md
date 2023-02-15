# Check for requirements:
* Install Pihole and its SSH Sever 
* Add the the final IPs the will be assigned to
* check for these Applications that needs to be installed:
 ```
 sudo apt install git rsync ssh sqlite3
 ```
 * Edit this file:
 ```sudo EDITOR=nano visudo```
 #comment out %sudo ALL(ALL:ALL) and add this line: 
 ```
 pihole ALL=(ALL) NOPASSWD:ALL
 ```
 ![image](https://user-images.githubusercontent.com/44326428/218896437-05643430-0ff1-48c2-8e6a-30775f7b3569.png) <br/>
 where pihole is the user name with admin rights, This process will omit the password input everytime he puts sudo in the begining. <br/>
 then reboot ```sudo reboot```
 
