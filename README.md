# Part4-Exercise1

### A)

###### Exercise1
- Construct type: Concrete class (contains main logic)
- Reason: It is the the main entry point which shows the use of Zipper and TestZipper and uses a try-with-resources block to ensure cleanup.


###### Zipper

- Construct type: Abstract class
- Reason: It provides a general structure for unzipping files but leaves createHandler unfinished so that other classes must complete it.

###### TestZipper

- Construct type: Concrete class (Concrete subclass of zipper)
- Reason:  It completes Zipper by defining how each file should be processed which makes it a fully working class.

###### Handler 

- Construct type: Abstract static inner class 
- Reason: It is a helper class inside Zipper that sets the rules for handling files but does not define how files should be handled, letting subclasses decide.

###### Anonymous Class (inside TestZipper#createHandler)

- Construct type: Anonymous subclass of Handler
- Reason: Since file handling logic is needed only once per file, defining a full class separately would be unnecessary. Instead an anonymous class provides a one time implementation of handle().


### B)

###### Exercise1
- Why: It serves as the entry point to demonstrate how Zipper and TestZipper work.
- Key features: Uses try-with-resources for proper cleanup.
- Why not others: Interfaces cannot have constructors and cannot instantiate objects.


###### Zipper
- Why:  It provides a reusable base for unzipping files while allowing subclasses to define custom file handling.
- Key features: Implements AutoCloseable for automatic resource cleanup and has abstract methods for flexibility and contains shared logic (creating, deleting temp directories, unzipping files). 
- Why not others: If Zipper was concrete, every subclass would have to use the same file handling logic which makes it less flexible. Additionaly, an interface cannot have implemented methods.

  
###### TestZipper
- Why: It applies a structure for file handlers inside Zipper while keeping it independent of Zipper instances.
- Key features: Overrides abstract methods to define behavior while reusing Zipper's unzipping logic.
- Why not others: If TestZipper was abstract, it would still need another subclass to be functional, making it unnecessary. Addtionaly, if TestZipper was a seprate class without Extending Zipper, it would need to rewrite the unzipping logic, making the code redundant.

  
###### Handler (inner class inside Zipper)
- Why: It applies a structure for file handlers inside Zipper while keeping it independent of Zipper instances.
- Key features: Specified as abstract thus subclasses must implement the handle method. Moreover, it is specified as static, making it independent of Zipper instances and preventing unnecessary dependencies.
- Why not others: If it was concrete, it would force all handlers to follow a fixed behavior, removing flexibility. Additionaly, an interface wouldn't work because Handler includes a constructor to initialize the file path.


###### Anonymous Inner Class (inside TestZipper#createHandler)
- Why: It defines file handling logic in place, avoiding unnecessary new class definitions.
- Key features: Implements handle dynamically inside TestZippe which reduces redundancy.
- Why not others: If the handler had a separate class, it would only be used in one place, which would make it unnecessary.


### C)

The temporary directory's lifespan is managed by the Zipper class, which creates it in the constructor (Files.createTempDirectory(...)) and deletes it in the close() method. Since Zipper implements AutoCloseable, the directory is automatically cleaned up when the object is closed, using a try-with-resources block in Exercise1. The Handler class and its anonymous subclass process files within the temporary directory but do not affect its lifespan since they exist only while Zipper is active. TestZipper extends Zipper, defining file handling behavior without modifying the directory’s lifecycle. Therefore, the directory exists only during the execution of Zipper and is removed once the process is complete. 


### D)

The class signature `protected abstract static class Handler` is structured this way to control access, apply required behavior, and keep it independent of Zipper instances. The protected keyword ensures that only Zipper and its subclasses (like TestZipper) can use or extend it. The abstract keyword makes Handler a template that must be extended by another class in order to ensure that each handler defines its own way of processing files. The static keyword is appropriate because Handler does not need access to any instance variables or methods from Zipper which means that it can be used without creating an instance of Zipper. This keeps the structure clean, avoids unnecessary dependencies, and allows file handlers to function independently while still being logically grouped within Zipper.











