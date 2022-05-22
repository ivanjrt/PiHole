# PiHole-Backup



To Add more List onto the PiHole go to this site: <br/>
https://firebog.net/ <br/>

Once you have achieve your ideal list. <br/>

here is how to back it up*. <br/>



Your current lists will be located in this path:<br/>
```Ruby
 ls /etc/pihole/ -lh | grep "list"
```

As for your current Database, I found them here:<br/>

``` Ruby
ls -lh /etc/pihole/pihole-FTL.db
```

Although for sanity sake I'd just save the entire folder ```/etc/pihole/```  via WINSCP or FileZilla




*_I have only compiled this information, -I have not tested Take it As-Is._<br/>
