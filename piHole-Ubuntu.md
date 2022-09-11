Install Ubuntu 21.04.
VM Requirements:
* 30 HDD more than enough
* 4GB Ram but when is set and done 2GB is plenty
* ubuntu-21.04-desktop-amd64.iso  (if one starts with 22 out of the box, then it hangs at the begining)

Update to whatever is available:
```
sudo apt update &&  apt upgrade
```

* SSH & Curl Installation to have easier control locally in a Terminal
```
sudo apt install openssh-server curl -y
```
 </br>you can now connect from Putty<br/>
**Disable udpates: **<br/>
	Open the settings for updates<br/>
	Search for ‘Software & Updates’<br/>
	Select the ‘Updates’ tab.<br/>
	Change ‘Automatically check for updates’ from ‘Daily’ to ‘Never‘.<br/>
	
* Pihole Install
```
curl -sSL https://install.pi-hole.net | bash
```
From here is basicaly Next next 'til the end, if any changes then press 'Space bar' to check
note: the last screen it will give you the password for the site, but you can always change it with ```pihole -a -p```

* Disable the GUI
	```
  systemctl set-default multi-user.target
	shutdown -r now
  ```

test the website and if success then shutdown the VM, Reserve the IP in the DHCP and then save it
```
systemctl poweroff -i	
```
	
Add Adlist from these two sites:
https://firebog.net/
https://obutterbach.medium.com/unlock-the-full-potential-of-pihole-e795342e0e36

At the bottom of the page make sure you add the subnet and router info:
![image](https://user-images.githubusercontent.com/44326428/189513495-a0ff9481-98d7-432d-9a5a-da8c1924c262.png)


Update the Database  Tools > Gravity, it might take a while or just restart the VM

To upgrade to a new PiHole Version. on the console type:
	pihole -up
Reboot the vm to make sure everything is legit! -Also mind as well take a snapshot of it as well

To update within Ubuntu:
 sudo apt update && sudo apt upgrade -y

