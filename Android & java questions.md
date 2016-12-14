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
