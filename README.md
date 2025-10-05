# Project-Slicing
Project build in C++.
You will complete a C++ program that prints 3D 
volumes made from shapes. The 3D volume is broken 
into 2D slices containing filament to be printed layer 
by layer. The shapes supported are spheres and cubes. 
For parts of the volume that are empty and below 
filament, support material can be added. Note that axes and orientations may vary among 
printers. 



Fret Class 
Each slice of the 3D volume is represented using a template class named Fret that stores 
a particular type of value (determined by its template parameter T) in each element of a 
2D array. Class member functions accept x and y positions starting at 0 (zero-based 
indices). The 2D array may have different x and y dimensions (it is rectangular). 
Values are currently stored internally using a statically-allocated 2D array, i.e., with 
constant (fixed-size) dimensions. 
y 
x 
Slices are shown in table rather than one after another as 
will be done by program. 
Supports (#) for 
next slice, i.e., 
filament (*) or 
other supports 
(#) above 
current slice. 
Support (#) for 
duplicated top 
of sphere (*) in 
next slice. 
z 
Nothing to 
print in last 
slice… 
Maybe try 
balancing a 
cube on 
top? 
Sphere extends 
radius (2) from 
center (number 
of elements 
discretized to 
2D array). 
Your task is to change the class to use a dynamically-allocated 2D array. For example: 
pattern   
[0]  
[1]  
[2]  
[3]  
[4]  
[0] [1] [2] [3] [4] 

Note: main program 
stores char at each 
position: 
• empty (.) 
• filament (*) 
• support (#) 
Fret has 2 overloaded subscript [ ] operators. The const version is only for accessing 
elements; the non-const version returns a reference so that elements may be assigned. 
Since subscripts only have 1 parameter, x and y must be passed as a pair<int, int>.  
Modify the data type of member pattern to be an appropriate pointer type to store a 
dynamic 2D array. Also change X_SIZE and Y_SIZE from constants to variables. 
Additionally, write the following: 
• Change the default constructor to instead take x and y dimensions and an initial value. 
Allocate a dynamic 2D array with those dimensions and store the initial value in all 
elements. 
• Add a copy constructor and assignment operator to copy the object as it now contains 
a dynamic 2D array. The code in the main program requires copying to work correctly. 
• Add a destructor to deallocate the dynamic 2D array and reset variables. 
Place output in any functions (copy constructor, assignment, const vs. non-const []) 
or set breakpoints with the Debugger if you need to see when they run. 
Main Program 
vector 
Since a Fret only represents a 2D slice of 
the 3D volume, the program will use a 
vector of Fret objects (see right). This 
illustrated array is an abstraction since the 
internal Fret objects are more complex. 
Note that variable slices is indexed by the 
z dimension, with lower indices for slices 
closer to the build plate. 
slices 

[0] 
[1] 
See the Sample Run to ensure you understand which are the x, y and z dimensions! 
… 
Page 3 of 4 
CSI218 – Data Structures and Algorithms – Spring 2025 
To make printing functional (see Sample Run), also complete the following in the main 
program: 
• Once you complete both constructors for class Fret above, you will need to make all 
the initial Fret objects in the vector the requested x and y size. 
• Write an overloaded operator << so that a Fret can be displayed. Once you do 
so, you may uncomment the code that prints out each slice at the end of the program. 
Ensure you display the x and y dimensions in the correct order. 
• drawSphere(): Place filament at any position in the 3D volume that meets the 
constraint for a filled sphere: (x – x0)² + (y – y0)² + (z – z0)² ≤ r². I.e., any position in 
which the distance from the center of the sphere (x0, y0, z0) is less than or equal to the 
radius (r). The equation uses the squares (2) to avoid computing square roots (√).  
• drawCube(): Place filament in the 3D volume using the constraints for a filled cube: 
|x - x0| <= r, |y - y0| <= r, and |z - z0| <= r. This is based on the cube center (x0, y0, z0) 
and each side’s half-length, which can also be called its radius (r).  
• addSupports(): Add support material below filament or other support material. 
• countMaterial(): Compute amount of material used, either filament or supports. 
• Complete option (e) to insert an empty slice below the requested slice. Ensure it works 
when adding a slice to the top. 
Standards 
Adhere to our standards for constants, variables, functions, classes, placement/alignment 
of code, and comments.  In particular, add comments to explain code that is not obvious.  
Fill in your name and date at the top of source code files you edit. 
