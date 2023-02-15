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
# Run the installer for Gravity sync:
* from the Main Pihole first, then the secondary after
```
curl -sSL https://raw.githubusercontent.com/vmstan/gs-install/main/gs-install.sh | bash
```
Then just add yes to secure the connection, it should look like this:
![image](https://user-images.githubusercontent.com/44326428/218898597-ec78e181-3918-43e0-aeab-e3b66510b686.png)

# Time to test things out, add a rule block in the main pihole:
 * gravity-sync compare
 * gravity-sync push
 * gravity-sync
 * ![image](https://user-images.githubusercontent.com/44326428/218904300-9557ef44-438a-4f55-aa59-a2f07c2d84b1.png)
and it should foward that blocklist

# To automate it 
```
gravity-sync auto quad
```
from the Master, which will sync every 15 Mins, although no sure so, I did this: <br/>
```crontab -e```
and Added this at the end
```
*/10 * * * * /bin/bash gravity-sync push
```

Notes:
to update gravity sync:
```
gravity-sync version
gravity-sync update
```
Commands without a password: https://linuxize.com/post/how-to-run-sudo-command-without-password/  <br/>
full manual on gravity: https://github.com/vmstan/gravity-sync <br/>
here's very old info but at least it has the flow of what needs to happen, https://www.youtube.com/watch?v=IFVYe3riDRA&t  <br/>

