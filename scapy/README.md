# Introduction to Scapy

Lets do a deep dive into networking by looking at individual packets. 

Please ignore any actual *assignment* part of this guide, it was a quick copy
over from a previous semester.  I hope it proves useful though ;)

---

## Background

So far the networking tools we have been using (`nc` and `nmap`) all perform a 
strict set of tasks, but many of the most basic networking attacks rely on the 
manipulation of packets.  We have yet to introduce a tool that truly lets us 
manipulate packets (easily).  Until now...

[Enter Scapy](https://scapy.net/).

---

> From [scapy.net](https://scapy.net/):
> Scapy is a powerful interactive packet manipulation program. It is able to forge
> or decode packets of a wide number of protocols, send them on the wire, capture
> them, match requests and replies, and much more. It can easily handle most
> classical tasks like scanning, tracerouting, probing, unit tests, attacks or
> network discovery (it can replace hping, 85% of nmap, arpspoof, arp-sk, arping,
> tcpdump, tethereal, p0f, etc.). It also performs very well at a lot of other
> specific tasks that most other tools can’t handle, like sending invalid frames,
> injecting your own 802.11 frames, combining technics (VLAN hopping+ARP cache
> poisoning, VOIP decoding on WEP encrypted channel, …), etc.

---

## Resources

* [The scapy python library](https://scapy.net/)
* [Scapy Docs](https://buildmedia.readthedocs.org/media/pdf/scapy/latest/scapy.pdf)
* [Scapy Unofficial Guide](https://theitgeekchronicles.files.wordpress.com/2012/05/scapyguide1.pdf)

---

## Installing Scapy

You can install scapy easily within
Anaconda python (or miniconda) with `conda install scapy`.  Scapy is also commonly
included in `apt` and other linux repositories.

```bash
sudo apt install python3-scapy
```

---

### Using Scapy interactively

Lets start by performing a basic tcpdump in scapy (and save it to a python
variable)!  Start the scapy ipython interface with the following:

```
sudo scapy
```

This should launch the scapy interface which looks like this:

```
                     aSPY//YASa       
             apyyyyCY//////////YCa       |
            sY//////YSpcs  scpCY//Pp     | Welcome to Scapy
 ayp ayyyyyyySCP//Pp           syY//C    | Version 2.4.2
 AYAsAYYYYYYYY///Ps              cY//S   |
         pCCCCY//p          cSSps y//Y   | https://github.com/secdev/scapy
         SPPPP///a          pP///AC//Y   |
              A//A            cyP////C   | Have fun!
              p///Ac            sC///a   |
              P////YCpc           A//A   | Craft me if you can.
       scccccp///pSP///p          p//Y   |                   -- IPv6 layer
      sY/////////y  caa           S//P   |
       cayCyayP//Ya              pY/Ya
        sY/PsY////YCc          aC//Yp 
         sc  sccaCY//PCypaapyCP//YSs  
                  spCPY//////YPSps    
                       ccaacs         
                                      
>>> 
```

---

From this point on we will be in an interactive python & scapy environmnt.

Most of the commands from here on out will be meant to be typed into scapy, *not
Bash*!

* To sniff some packets we are going to use the scapy `sniff()` function
  ```
  capture = sniff(count=10)
  ```

This will sniff 10 packets and store them in capture.  We can print out some
details regarding these packets with the following commands:
* `capture`
* `capture.show()`
* `capture[1]`
* `capture[9].show()`

---

###### More work

* Play around with the above and look at at least 2 visibly different packets (try
  to find a TCP and a UDP or an ICMP packet).

---

### Lets build a packet!

Scapy provides some awesome tools for packet creation.  Lets look at a few of them:

* `ls()` list available layers OR info on a given layer name (example: `ls(IP)`)
* `lsc()` list available scapy commands
* `IP()` create an IP packet layer
* `TCP()` and `UDP()` both create their respective packet layers
* `show()` and `summary()`

So lets make a packet!
For this example we will be creating a simple DNS queuery

There are a good number of steps so follow along and feel free to play
around (we aren't sending these packets anywhere yet, we're just playing).

1. First lets create an IP packet with just `IP()`.  In scapy:
   ```
   ofp = IP()
   ofp.show()
   ```
   Easy right?  `ofp` is just the variable name I chose for *Our First Packet*
   (sorry...)

2. Lets make this IP more useful for our test DNS case and give it a
   destination of a nameserver.  If you are on campus you MUST use a campus
   nameserver like `130.108.128.200`, otherwise I would just use a google DNS
   server such as `8.8.8.8`:
   ```
   ofp = IP(dest="8.8.8.8")
   ```

   ummm...`ls(IP)`

   ```
   ofp.show()
   ```

   Now we are getting somewhere.  But there isn't much in an IP packet itself
   besides source and destination addresses (we can check what needs to go in the
   IP section with `ls(IP)`.

3. Now lets get to some of the good stuff.  In order to get our DNS request to the
   server we need to add a UDP layer, which in scapy is done like so:
   ```
   ofudp = ofp/UDP()
   ```
   **OR**
   ```
   ofudp=IP(dest="8.8.8.8")/UDP()
   ```

   Here we have created a new packet from the IP layer contained in `ofp` and the
   `UDP()` scapy command.  Lets take a look at our two packets now:
   ```
   ofp.show()
   ofudp.show()
   ```

4. Looking good so far, but we're missing all of the DNS data in the UDP datagram.
   Luckily scapy has a library for this too:
   ```
   ofdnsp=ofudp/DNS()
   ofdnsp.show()
   ```
   We're almost there, but I wanted to take a second to show you that the DNS()
   created an empty shell of the DNS UDP datagram.  To fill that out we need to
   enter the necessary information into the scapy `DNS()` field which I do not
   expect you to know (however you should be able to capture an example with
   tcpdump or scapy and evaluate it).

5. Finally we add the neccessary data to our UDP DNS datagram.  
   To make things easier on you I am just providing the correct options below:
   ```
   ofdns= ofudp/DNS(rd=1,qd=DNSQR(qname="www.google.com"))
   ```

Before sending we should look at our packet to make sure that it has all of the
correct data (or at least to make sure there is something new since the last
time ;)

```
ofdns.show()
```

Which should hopefully show a fully formed packet that could be sent.

---

###### Special task

* Write a one line packet creation for step 5 above (that does *not* rely on
  previously created variables)

---

### Send that packet (and receive a response)

We will be unsing the scapy `sr()` to send and recieve packets.  We will also
create a `response` to store any packets send in respone to our request.

```
response = sr(ofdns)
```

Let that run for a few seconds (if it doesn't stop automatically stop it with
`Ctrl + C`).

Lets check our response!  We should be able to see what was returned to us via
one of the following:

```
response[0]
```

which should show the first packet received.  Hopefully this is a response to
our DNS queuery.  

