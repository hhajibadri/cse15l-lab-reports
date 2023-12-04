# Lab Report 5

Student: Hi everyone, I am having trouble locating and fixing a bug inside my program. My program has three methods, this only concerns one of them. This method is supposed to calculate the average of an array type of double without considering the minimum value. It is not working correctly.

TA: Try using the JDB to step through your program to figure out where the problem is. First compile with the special flag `java -g example.java` and then run JDB `jdb example.java`. You would want to set a breakpoint at the beginning of that method and step through each line to figure out how the values are being computed or updated.






# Reflection

Something interesting I learned in the second half of the quarter was vim. Before learning about vim I always wondered if there was a way to do everything from the command line and it turned out there was. You can read, write, copy, and paste all from the command line. Although I am glad we have a graphical interface in todays day and age it was cool to see how manual things were back then in the beginning. Another thing I learned from the tutor is when compiling java treats the last expression as the class name. So for example if I typed in something like `java ~/Main` it doesn't handle paths it just treats `~/Main` as a name itself.