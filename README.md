# PiHole-Backup

To Add more List onto the PiHole go to this site: <br/>
https://firebog.net/ <br/>
https://obutterbach.medium.com/unlock-the-full-potential-of-pihole-e795342e0e36<br/>

Here is how to back it up*. <br/>

![image](https://user-images.githubusercontent.com/44326428/218639215-ae044476-d835-4b8e-84a6-9be89204fd99.png) <br/>

then Restore: <br/>
![image](https://user-images.githubusercontent.com/44326428/218639514-7d30a211-a7f4-445d-b12e-0762e49ef1b4.png) <br/>

then Update Gravity: <br/>
![image](https://user-images.githubusercontent.com/44326428/218639704-c81fc3b2-43b0-4215-9e83-b2721d3d28e4.png)

# Fix Ubuntu partitions, showing small size:
```
sudo lvextend --resizefs -l +100%FREE ubuntu-vg/ubuntu-lv
```
