# Design-Pattern-Singleton
 
Ensure a class only has ONE INSTANCE,and provide global point of access to it.

Usages:
- Restrict resource use(instead of creating numbers of large objects without limit)
- When you have a sensitive object whose data shouldn't be accessed by multiple instances(such as a registry).
- When multithreading and you don't want conflicts in how the data behind that object is accessed.

Make the constructor PRIVATE.
This stops anyone's code from using the new operator,except for code inside Database class.
You give your class a constructor with no public access and let the rest of the world create objects with a UTILITY METHOD that calls that constructor behind the scenes.
You can also add code to the utility method to make sure that no more than one object exists.

The usual name for that method when you're using the Singleton pattern is getInstance(or createInstance, or a more specific name such as createDatabase).
This method should be PUBLIC and STATIC so you just call the Database class's name for example: Database.getInstance()



Warning: If two threads are making the test " if(singleObject == null) " at the same time, and no Database object exists yet,
they both can get past it, which means both threads will create a Database object.
Use synchronized keyword,which you can use to restrict access to getInstance to one thread at a time.(SEE DESIGN-PATTERN-SINGLETON-SYNCHRONIZED)
