# Part4-Exercise1

### A)

###### Exercise
- Construct type: Concrete class
- Reason: it servers as an entry point for executing the program. It initializes the TestZipper instance using a try-with-resources block to ensure proper resource management.

###### Zipper

Construct type: Abstract class
Reason: It provides a general framework for handling ZIP file extraction while leaving the file processing logic to subclasses via an abstract method createHandler(Path file).

###### TestZipper

Construct type: Concrete subclass of Zipper
Reason: It specializes Zipper by implementing createHandler(Path file) whic defines how extracted files should be processed.

###### Handler (inner class inside Zipper)

Construct type: Abstract static inner class
Reason: It represents an abstraction for handling files. Each file has its own handler instance, but the logic for handling files is defined in subclasses.

###### Anonymous Inner Class (inside TestZipper#createHandler)

Construct type: Anonymous subclass of Handler
Reason: Since file handling logic is needed only once per file, defining a full class separately would be unnecessary. Instead, an anonymous class provides a one time specialized implementation of handle().


### B)

###### Exercise
- Why: Exercise1 is the entry point of the program, meaning it needs to execute the main logic.
- Key features: Uses try-with-resources for proper cleanup.
- Why not others: Interfaces cannot have constructors and cannot instantiate objects.


###### Zipper
- Why: 
- Key features:
- Why not others:

  
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


