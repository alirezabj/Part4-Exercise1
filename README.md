# Part4-Exercise1

### A)

###### Exercise1
- Construct type: Concrete class (contains main logic)
- Reason: It is the the main entry point which shows the use of Zipper and TestZipper, and uses a try-with-resources block to ensure cleanup.


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
- Why: Exercise1 is the entry point of the program, meaning it needs to execute the main logic.
- Key features: Uses try-with-resources for proper cleanup.
- Why not others: Interfaces cannot have constructors and cannot instantiate objects.


###### Zipper
- Why:  It provides a reusable base for unzipping files while allowing subclasses to define custom file handling.
- Key features: Implements AutoCloseable for automatic resource cleanup and has abstract methods for flexibility and contains shared logic (creating, deleting temp directories, unzipping files). 
- Why not others: If Zipper was concrete, every subclass would have to use the same file handling logic which makes it less flexible. Additionaly, an interface cannot have implemented methods.

  
###### TestZipper
- Why: 
- Key features:
- Why not others:

  
###### Handler (inner class inside Zipper)
- Why: 
- Key features:
- Why not others:


###### Anonymous Inner Class (inside TestZipper#createHandler)
- Why: 
- Key features:
- Why not others:


