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
![image](https://github.com/ivanjrt/PiHole-Backup-Ubuntu/assets/44326428/b417d823-2cf1-4099-8bb0-e90aeca25b3f) <br/>
 where pihole is the user name with admin rights, This process will omit the password input everytime he puts sudo in the begining. <br/>
 then reboot ```sudo reboot```
# Run the installer for Gravity sync:
* from the Main Pihole first, then the secondary after
```
curl -sSL https://raw.githubusercontent.com/vmstan/gs-install/main/gs-install.sh | bash
```
Then just add yes to secure the connection, it should look like this: <br/>
it will ask you for the IP of the secondary PiHole and the username, and at the end it will run its first sync and will show result<br/>
![image](https://github.com/ivanjrt/PiHole-Backup-Ubuntu/assets/44326428/309516a7-4ec5-4563-b935-20ea29627f7c)<br/>


# Time to test things out, add a rule block in the main pihole:
 * `gravity-sync compare`
 * `gravity-sync push` it will push from itself to the remote pihole
 * `gravity-sync pull` it will pull from itself to the remote pihole
 * `gravity-sync` both
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

