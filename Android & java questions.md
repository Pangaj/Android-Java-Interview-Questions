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



###2. Mention some ___web protocols___ used for world wide web

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


###3. What is difference between Asynchronous vs synchronous in Thread operations?

* When you execute something __synchronously__, you ___wait for it to finish before moving on to another task.___ 
* When you execute something __asynchronously__, you can ___move on to another task before it finishes.___

* That being, said, in the context of computers this translates into executing a process or task on another "thread." __A thread is a series of commands--a block of code--that exists as a unit of work.__
*  The operating system can manage multiple threads and assign a thread a piece ("slice") of processor time before switching to another thread to __give it a turn to do some work.__ At its core, a processor can simply execute a command--it has no concept of doing two things at one time. The operating system simulates this by allocating slices of time to different threads.

##### After Multiple cores/processors
* Now, if you introduce multiple cores/processors into the mix, then things ___can actually happen at the same time___. 
* The operating system __can allocate time to one thread on the first processor__, then __allocate the same block of time to another thread on a different processor.__

######Synchronous (one thread):
```
1 thread ->   |<---A---->||<----B---------->||<------C----->|
```

######Synchronous (multi-threaded):
```
thread A -> |<---A---->|   
                        \  
thread B ------------>   ->|<----B---------->|   
                                              \   
thread C ---------------------------------->   ->|<------C----->| 
```

######Asynchronous (one thread):
```
         A-Start ------------------------------------------ A-End   
           | B-Start -----------------------------------------|--- B-End   
           |    |      C-Start ------------------- C-End      |      |   
           |    |       |                           |         |      |
           V    V       V                           V         V      V      
1 thread->|<-A-|<--B---|<-C-|-A-|-C-|--A--|-B-|--C-->|---A---->|--B-->| 
```

######Asynchronous (multi-Threaded):
```
 thread A ->     |<---A---->|
 thread B ----->     |<----B---------->| 
 thread C --------->     |<------C--------->|
```

* Here, Start and end points of tasks A, B, C represented by ```<``` , ``` >``` characters.

* CPU time slices represented by vertical bars ```|```


###4. Can try/catch block is executed without executing the finally block?

* __Note,__ The ___finally___ block will always execute. 
* But it wont run if you call ___System.exit()___ from try/catch block

* If you even use ___return___ statement in the try/catch block, the finally block will execute. Only the ___finally___ can be skipped when you use ___System.exit()___ in you try/catch block.


###5. Difference between String object and String literal?

* Before going to the answer, we want to know that,
* __String object__ - ___Variable___ But, __String literal__ - ___Constant.___

* When you use a **string literal the string can be interned**, but when you use **new String("...") you get a new string object.**


```
String a = "Pan"; 
String b = "Pan";
System.out.println(a == b);  // true
```

* The above example refers the same object.


```
String c = new String("Pan");
String d = new String("Pan");
System.out.println(c == d);  // false

```

* 2 different objects are created and they have different references.

* In general, you should use the **string literal notation when possible**. It is *easier to read* and it gives the compiler a chance to optimize your code.