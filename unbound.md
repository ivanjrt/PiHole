After Installing PiHole, and making sure it works
source: https://docs.pi-hole.net/guides/dns/unbound/
https://www.techaddressed.com/tutorials/pi-hole-recursive-dns-unbound/ <br/>
```sudo apt install unbound -y```<br/>
```sudo nano /etc/unbound/unbound.conf.d/pi-hole.conf```<br/>
Add this to that file:
```
server:
    # If no logfile is specified, syslog is used
    # logfile: "/var/log/unbound/unbound.log"
    verbosity: 0

    interface: 127.0.0.1
    port: 5335
    do-ip4: yes
    do-udp: yes
    do-tcp: yes

    # May be set to yes if you have IPv6 connectivity
    do-ip6: no

    # You want to leave this to no unless you have *native* IPv6. With 6to4 and
    # Terredo tunnels your web browser should favor IPv4 for the same reasons
    prefer-ip6: no

    # Use this only when you downloaded the list of primary root servers!
    # If you use the default dns-root-data package, unbound will find it automatically
    #root-hints: "/var/lib/unbound/root.hints"

    # Trust glue only if it is within the server's authority
    harden-glue: yes

    # Require DNSSEC data for trust-anchored zones, if such data is absent, the zone becomes BOGUS
    harden-dnssec-stripped: yes

    # Don't use Capitalization randomization as it known to cause DNSSEC issues sometimes
    # see https://discourse.pi-hole.net/t/unbound-stubby-or-dnscrypt-proxy/9378 for further details
    use-caps-for-id: no

    # Reduce EDNS reassembly buffer size.
    # IP fragmentation is unreliable on the Internet today, and can cause
    # transmission failures when large DNS messages are sent via UDP. Even
    # when fragmentation does work, it may not be secure; it is theoretically
    # possible to spoof parts of a fragmented DNS message, without easy
    # detection at the receiving end. Recently, there was an excellent study
    # >>> Defragmenting DNS - Determining the optimal maximum UDP response size for DNS <<<
    # by Axel Koolhaas, and Tjeerd Slokker (https://indico.dns-oarc.net/event/36/contributions/776/)
    # in collaboration with NLnet Labs explored DNS using real world data from the
    # the RIPE Atlas probes and the researchers suggested different values for
    # IPv4 and IPv6 and in different scenarios. They advise that servers should
    # be configured to limit DNS messages sent over UDP to a size that will not
    # trigger fragmentation on typical network links. DNS servers can switch
    # from UDP to TCP when a DNS response is too big to fit in this limited
    # buffer size. This value has also been suggested in DNS Flag Day 2020.
    edns-buffer-size: 1232

    # Perform prefetching of close to expired message cache entries
    # This only applies to domains that have been frequently queried
    prefetch: yes

    # One thread should be sufficient, can be increased on beefy machines. In reality for most users running on small networks or on a single machine, it should be unnecessary to seek performance enhancement by increasing num-threads above 1.
    num-threads: 1

    # Ensure kernel buffer is large enough to not lose messages in traffic spikes
    so-rcvbuf: 1m

    # Ensure privacy of local IP ranges
    private-address: 192.168.0.0/16
    private-address: 169.254.0.0/16
    private-address: 172.16.0.0/12
    private-address: 10.0.0.0/8
    private-address: fd00::/8
    private-address: fe80::/10
```
Restarting the service<br/>
```sudo service unbound restart```<br/>
Checking for the first time a request, If issues restart the Pihole Host<br/>
```dig pi-hole.net @127.0.0.1 -p 5335```<br/>

```sudo nano /etc/dnsmasq.d/99-edns.conf```<br/>
Add this:<br/>
```
edns-packet-max=1232
```
Test Validation<br/>
```dig fail01.dnssec.works @127.0.0.1 -p 5335```<br/>
```dig dnssec.works @127.0.0.1 -p 5335```<br/>
The first command should give a status report of SERVFAIL and no IP address. The second should give NOERROR plus an IP address.

Back to PiHole:<br/>
![image](https://user-images.githubusercontent.com/44326428/200484961-4407e0e9-a96e-4c2c-9ef5-7995dbd38063.png)
```127.0.0.1#5335```<br/>
logging to unbound<br/>
```sudo nano /etc/unbound/unbound.conf.d/pi-hole.conf```
Add this but omit **server:   the command just go underneath**<br/>

```
server:
    # If no logfile is specified, syslog is used
    logfile: "/var/log/unbound/unbound.log"
    verbosity: 1
```
![image](https://user-images.githubusercontent.com/44326428/218625265-83a16621-fb19-426f-b881-f86fce5e9ded.png)<br/>
```
sudo mkdir -p /var/log/unbound
```
```
sudo touch /var/log/unbound/unbound.log
```
```
sudo chown unbound /var/log/unbound/unbound.log
```
```
sudo service unbound restart
```

    




