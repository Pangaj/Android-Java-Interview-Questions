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



###2. Mention some ___web protocols___ used for world wide web.

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


###6. Differnce between Stack and Heap in memory allocation.

* **Stack** is used for ***Static memory allocation,*** Where **Heap** is used for ***Dynamic memory allocation,*** both stored in computer's RAM.

######Stack
* Variables allocated on the **stack** are **stored directly to the memory** and ***access to this memory is very fast***, and it's allocation is dealt(deal) with when the program is compiled. 
* When a function or a method calls another function which in turns calls another function etc., the execution of all those functions remains suspended until the *very last function returns its value*. The stack is always reserved in a **LIFO** *(Last in first out)* order, the most recently reserved block is always the next block to be *freed*. 
* This makes it really *simple to keep track of the stack*, freeing a block from the stack is **nothing more than adjusting one pointer.**

######Heap
* Variables allocated on the **heap** have their ***memory allocated at run time*** and ***accessing this memory is a bit slower***, but the *heap size is* ***only limited by the size of virtual memory.***
* **Element of the heap have no dependencies with each other** and can always be ***accessed randomly at any time***. You can *allocate and free a block at any time.* 
* This makes it much *more complex to keep track* of which parts of the heap are *allocated or free at any given time.*

######Stack or Heap
* You can use the **stack** if you *know exactly how much* **data** you need to allocate before **compile time** and it is ***not too big.***
* You can use **heap** if you *don't know exactly how much* **data** you will need at **run-time** or if you need to allocate a ***lot of data.***

######Multi-threaded situation
* In a multi-threaded situation **each thread** will have its **own completely independent stack** but they will ***share the heap***. 
* **Stack** is ***thread specific*** and,
*  **Heap** is ***application specific.*** 
*  The **stack** is *important to consider* in ***exception handling and thread executions.***

####7. Compare the sleep() and wait() methods in threads.

* ***sleep()*** is a *blocking operation that keeps* a **hold on the monitor** / **lock of the shared object** for the *specified number of milliseconds.*

* ***wait(),*** **simply pauses the thread** until either,

1. The **specified number of milliseconds** have elapsed or 
2. It **receives a desired notification from another thread** *(whichever is first),* **without keeping a hold on the monitor/lock** *of the shared object.*

* ***sleep()*** is most commonly **used for polling, or to check for certain results, at a regular interval.** 
* ***wait()*** is generally used in **multithreaded applications**, *in conjunction with notify() / notifyAll(), to* **achieve synchronization** *and avoid race conditions*

###8. ```ArrayList```, ```LinkedList```, and ```Vector``` are all implementations of the ```List``` interface. Which one of them is most efficient for adding and removing elements from list?

*  ***LinkedList*** gives you the best performance.
*  **ArrayList** and **Vector** each use an *array to store* **the elements of the list**. 
*  As a result, when an element is *inserted into (or removed from)* the *middle of the list*, the elements that follow **must all be shifted accordingly**. 
*  ***Vector is synchronized***, so if a *thread-safe implementation is not needed*, it is *recommended* to use **ArrayList** rather than Vector.
*  **LinkedList**, on the other hand, is **implemented using a doubly linked list.** As a result, an *inserting or removing* an element only requires ***updating the links that immediately precede*** and *follow the element being inserted or removed*.
*  However, it is worth noting that if **performance is that critical**, it’s *better to just use an array and manage it yourself*, or use one of the *high performance 3rd party packages* such as [***Trove***](http://trove.starlight-systems.com) or [***HPPC***](http://labs.carrotsearch.com/hppc.html).


###9. Why would it be more secure to store sensitive data (such as a password, social security number, etc.) in a ```character array``` rather than in a String?

* In Java, **Strings are immutable** and are ***stored in the String pool***. 
* What this means is that, once a *String is created*, it ***stays in the pool in memory until being garbage collected***. 
* Therefore, e*ven after you’re done processing the string value* (e.g., the password), it **remains available in memory for an indeterminate period of time** thereafter (again, until being garbage collected) **which you have no real control over**. 

> Therefore, anyone having **access to a memory dump** can potentially *extract the sensitive data* and exploit it.

* In contrast, *if you use* a **mutable object** like a ***character array***, to store the value, you ***can set it to blank once you are done with it*** with confidence that **it will no longer be retained in memory.**


###10. Difference between List and Set in Java?
* They both are useful interface collections
* **List** - ***allows duplicate element***, but **Set** - ***don't allows duplicate elements***
* *List* **maintains** the ***insertion order*** of element, - but *Set* is ***unordered collection***
* *List* can have **many null objects** - but *Set* permit **only one null element**

###11. Can you override private or static method in Java ?
* We **can not** override private or static method in Java, if we create **similar method** with **same return** type and same method **arguments** that's called ***method hiding***.

###12. What will happen if we put a key object in a HashMap which is already there ?
> If we put the same key again, then it will **replace the old mapping** because ***HashMap doesn't allow duplicate keys***.


###13. If a method throws NullPointerException in super class, can we override it with a method which throws RuntimeException?
* We **can very well throw super class of RuntimeException** in ***overridden method*** but you ***can not do same if its checked Exception***.


###14. How do you ensure that N thread can access N resources without deadlock
* Key point here is **order**.
* If you **acquire resources in a particular order** and **release resources in reverse order** you can prevent deadlock.

###15. Can you access non static variable in static context?
* No you **can not** access static variable in non static context in Java.


###16. What is intent?
* It is  a kind of **message or information** that is **passed to the components**.
* It is used to launch an activity, display a web page, send sms, send email etc. There are two types of intents in android:
 1.     Implicit Intent
 2.     Explicit Intent

###17.What is implicit intent in android?
* Implicit intent is used to **invoke the system components**.



###18. What is explicit intent in android?
* Explicit intent is used to **invoke the activity class**.


###19. What is service in android?
* A [***service***](http://www.javatpoint.com/android-service-tutorial) is a **component that runs in the background**. It is used to play music, handle network transaction etc.


###20. What is AAPT?
* AAPT is an acronym for **Android asset packaging tool**. It handles the **packaging process**.


###21. What is content provider?
* Content providers are used to **share information between android applications**.

###22. What is fragment?
* Fragment is a **part of Activity**. By the help of fragments, **we can display multiple screens on one activity.**


###23. What is ADB?
* ADB stands for **Android Debug Bridge**. It is a *command line tool* that is used to **communicate with the emulator instance**.

###24. What is NDK?
* NDK stands for **Native Development Kit**. By using NDK, you can **develop a part **of app using** native language such as C/C++ to boost the performance**.

###25. What is ANR?
ANR stands for **Application Not Responding**. It is a dialog box that **appears if the application is no longer responding**.
