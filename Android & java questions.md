#Android & Java Questions

###1. What is difference between String, StringBuilder, StringBuffer?

* Before going to the question we must know what is _mutable_ and _immutable_ 

#####Immutable 
* the value stored in the String object cannot be changed.
* Example : String is Immutable

```
String str = "Pangaj";
str = str + " Shruthi";
```
* Although we made use of the same object(str), internally a new object was created in the process. So, if you were to do some string operation involving an append or trim or some other method call to modify your string object, you would really be creating those many new objects of class String.

* This will causes performance issue.


#####Mutable 
* the value stored in the String object can be changed.
* Example : StringBuilder and StringBuffer is mutable.

```
StringBuilder str = "Pangaj";
str = str.append(" Shruthi");
```

Now lets see the difference between the StringBuilder and StringBuffer:

* StringBuffer and StringBuilder have the same methods with one difference and that’s of ___synchronization___. 
* ___StringBuffer___ is __synchronized__( which means it is thread safe and hence you can use it when you implement threads for your methods) whereas ___StringBuilder___ is __not synchronized__( which implies it isn’t thread safe).

#####So, if you aren’t going to use threading then use the StringBuilder class as it’ll be more efficient than StringBuffer due to the absence of synchronization.



###2. Mention some web protocols used for world wide web

* __FTP__ : File Transfer Protocol
* __HTTP__ : Hypertext Transfer Protocol
* __IP__ : Internet Protocol
* __DNS__ : Domain Name Service
* __TCP__ : Transmission Control Protocol
* __SMTP__ : Simple Mail Transfer Protocol
* __SSL__ : Secure Sockets Layer
* __SSH__ : Secure Shell
* __ARP__ : Address Resolution Protocol
* __DHCP__ : Dynamic Host Configuration Protocol
* __DSN__ : Data Source Name
* __IMAP__ : Internet Message Access Protocol
* __ICMP__ : Internet Control Message Protocol
* __IDRP__ : ICMP Router-Discovery Protocol
* __IRC__ : Internet Relay Chat Protocol
* __POP3__ : Post Office Protocol version 3
* __PAR__ : Positive Acknowledgment and Retransmission
* __RLOGIN__ : Remote Login
* __TELNET__ : TCP/IP Terminal Emulation Protocol
* __UPD__ : User Datagram Protocol
* __UPS__ : Uninterruptible Power Supply