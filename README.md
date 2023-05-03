Download Link: https://assignmentchef.com/product/solved-cs1027-foundations-of-computer-science-ii-assignment-4
<br>
5/5 - (2 votes)

<span style="font-size: 2.61792em; letter-spacing: -1px; font-family: -apple-system, BlinkMacSystemFont, 'Segoe UI', Roboto, Oxygen-Sans, Ubuntu, Cantarell, 'Helvetica Neue', sans-serif;">Purpose</span>

To gain experience with

<ul>

 <li>The solution of problems using circular arrays and queues</li>

 <li>The design of algorithms in pseudocode and their implementation in Java.</li>

</ul>




<h1>1. Introduction</h1>

For this assignment you will be given a map and you are required to write a program that finds a path from a starting location to a destination, if such a path exists. This assignment is similar to Assignment 2, except that this time you are required to find a shortest path from the starting location, the Middlesex College building, to the destination, your house. As in Assignment 2 the map is divided into the same set of rectangular cells:

<ul>

 <li>A starting map cell, where the Middlesex College building is located.</li>

 <li>A destination map cell where your house is situated.</li>

 <li>Map cells containing blocks of houses or parks, where cars cannot drive.</li>

 <li>Map cells containing roads, where cars can drive. There are several types of road cells:

  <ul>

   <li>Road intersections; up to four different roads can converge into a road intersection. A car coming into an intersection can turn in any direction where there is a road</li>

   <li>North road, south road, east road, and west road cells. All these roads are one-way roads.</li>

  </ul></li>

</ul>

Figure 1 shows an example of a map divided into cells and a shortest path from the starting map cell to the destination.

Each map cell has up to 4 neighboring cells indexed from 0 to 3. Given a cell, the north neighboring cell has index 0, the east neighboring cell has index 1, the south neighbor has index 2, and the west neighbor has index 3.

<h1>2. Classes that You Need to Implement</h1>

A description of the classes that you need to implement in this assignment is given below. You can implement more classes, if you want. You <strong>cannot</strong> use any static instance variables. The data structure that you must use for this assignment is an ordered list implemented using a circular array, as described in the next section.

You <strong>cannot</strong> use any of the other java classes from the Java library that implement collections (i.e. you cannot use any java class that can store a set of 2 or more values).

<h2>2.1 CellData.java</h2>

This class represents the data items that will be stored in the circular array. Each object of this class stores two things: an identifier and a value. This class will be declared as follows:

<em>public class CellData&lt;T&gt; </em>

This class will have two instance variables:

<ul>

 <li><em>private T id</em>. A reference to the identifier stored in this object/</li>

 <li><em>private int value</em>. This is the value of the data item stored in this object.</li>

</ul>

You need to implement the following methods in this class:

<ul>

 <li><em>public CellData(T theId, int theValue). </em>Constructor for the class. Initializes <em>id</em> to <em>theId</em> and value to <em>theValue</em>.</li>

 <li><em>public int getValue().</em> Returns instance variable <em>value</em>.</li>

 <li><em>public T getId().</em> Returns instance variable <em>id</em>.</li>

 <li><em>public void setValue(int newValue).</em> Assigns newValue to instance variable <em>value</em>.</li>

 <li><em>public void setId(T newId).</em> Assigns the value of <em>newId</em> to instance variable <em>id</em>.</li>

</ul>




<strong>Figure 1. </strong>

<h2>2.2 OrderedCircularArray.java</h2>

This class implements an ordered list using a circular array. This class must implement the interface <em>SortedListADT.java.</em> The header of this class must be this:

<em>public class OrderedCircularArray&lt;T&gt; implements SortedListADT&lt;T&gt; </em>

You can download <em>SortedListADT.java</em> from the course’s website. This class must have the following private instance variables:

<ul>

 <li><em>private CellData</em>[]<em> list</em>. This array will store the data items of the ordered list.</li>

 <li><em>private int front</em>. This variable stores the <strong>position of the first data item</strong> in the list; this is the data item with the smallest value. In the constructor of this class this variable must be initialized to 1.</li>

</ul>

Note that this is different from the way in which the variable <em>front</em> is initialized in the lecture notes.<em> private int rear. </em>This is the index of the <strong>last</strong> data item in the ordered list; this is the data item with the largest value. In the constructor for this class this variable must be initialized to 0. Again, note that this is different from the way in which variable <em>rear</em> is used in the lecture notes.

<ul>

 <li><em>private int count</em>. The value of this variable is equal to the number of data items in the list.</li>

</ul>

Circular array <em>list</em> stores objects of the class <em>CellData</em>. These objects are kept sorted in the array according to their integer <em>value</em> attributes. An example of the array <em>list</em> storing 3 <em>CellData</em> objects in order of their integer values is shown in the next page.

This class needs to provide the following public methods.

<ul>

 <li><em>public OrderedCircularArray().</em> Initializes the instance variables as specified above. Array <em>list</em> must initially have length 5.</li>

</ul>

Note that when initializing array <em>list</em> as <em>list</em> = <em>new CellData&lt;T&gt;</em>[5]; the compiler will issue an error message because type <em>T</em> is not known at compilation time. To solve the problem use casting (create an array of type <em>CellData</em>[] and then cast it to the type that you need).

<ul>

 <li><em>public void insert (T id, int value)</em>. Adds a new <em>CellData object</em> storing the given <em>id</em> and <em>value</em> to the ordered list. You must ensure that after adding this new <em>CellData</em> object the list remains sorted. Note that <strong>the value of front must not change</strong> when adding a new <em>CellData</em> object into the list.</li>

</ul>

For example, if the array <em>list</em> is the following




and we invoke <em>insert</em>(“id 4”, 1), then the new array must be as follows




If the array is full when the <em>insert</em> method is invoked, a new array of size twice as large as the original one must be created, and the information from the old array must be copied there. <strong>You must ensure that the value of front does not change</strong>. So, if in the above array with 5 elements we invoke <em>insert</em>(“id 5”,2), the new array must be as follows




<ul>

 <li><em>public int getValue(T id) throws InvalidDataItemException</em>. Returns the integer value of the <em>CellData</em> object with the specified <em>id</em>. An <em>InvalidDataItemException</em> is thrown if no <em>CellData</em> object with the given <em>id</em> is in the ordered list. In this assignment we will assume that no two <em>CellData</em> objects in the ordered list have the same <em>id</em>.</li>

</ul>

Note that to check whether an object with the given<em> id</em> is in the ordered list you need to scan the ordered list using linear search. To check if the <em>CellData</em> object stored in some position of the ordered list has the same id attribute as <em>id</em> you must use the <em>equals</em> method, not the “==” operator. • <em>public void remove(T id) throws InvalidDataItemException</em>. Removes from the ordered list the <em>CellData</em> object with the specified <em>id</em>. An <em>InvalidDataItemException</em> is thrown if no <em>CellData</em> object in the ordered list has the specified <em>id</em>. Note that the value of front must not change when removing a data item from the ordered list using this method.

<ul>

 <li><em>public void changeValue (T id, int newValue) throws InvalidDataItemException</em>. Changes the <em>value</em> attribute of the <em>CellData</em> object with the given <em>id</em> to the specified <em>newValue</em>. An <em>InvalidDataItemException</em> is thrown if no object in the ordered list has the given <em>id</em>. After changing the value of the <em>CellData</em> obejct, you need to ensure that the list is still sorted by value, so you might have to reorder some of the information stored in the circular array.</li>

</ul>

<em>Hint</em>. First remove the <em>CellData</em> object with the given <em>id</em> and then add a new <em>CellData</em> item with the given <em>id</em> and <em>newValue</em>.

<ul>

 <li><em>public T getSmallest() throws EmptyListException</em>. Removes and returns the <em>id</em> or the <em>CellData</em> object in the ordered list with smallest associated value. Note that this is the <em>CellData</em> object stored in the position of the circular array specified by <em>front</em>. An <em>EmptyListException</em> is thrown if the list is empty. Note that for this method the value of <em>front</em> must change once the <em>CellData</em> object with smallest value has been removed.</li>

 <li><em>public boolean isEmpty()</em>. Returns <em>true</em> if the ordered list is empty and it returns <em>false</em></li>

 <li><em>public int size(). </em>Returns the number of data items in the ordered list.</li>

 <li><em>public int getFront().</em> Returns the value of instance variable</li>

 <li><em>public int getRear(). </em>Returns the value of instance variable</li>

</ul>

<em>front                                          rear </em>

0                         1                          2                          3                          4

To make sure you understand the above methods, consider the above ordered list where each entry stores a <em>CellData</em> object in which the <em>id</em> attribute is of type String. Initially the list was empty, and the value of <em>front</em> was 1, then method <em>insert</em> was invoked 3 times to add the 3 <em>CellData</em> objects shown. Note how <em>front</em> did not change and the entries are sorted by the integer attribute <em>value</em> of the <em>CellData</em> objects. If we invoke on this <em>list</em> method <em>getDataValue</em> (“id 2”), this method should return the value 8, while invoking <em>getDataValue</em>(“id 4”) should throw an <em>InvalidDataItemException</em>. Invoking <em>changeValue</em>(“id 2”, 0) will set the integer value stored in <em>list</em>[2] to 0. Since now the <em>CellData</em> objects are not in increasing order of value, the <em>CellData</em> object “id 2”, 0 needs to move to the front of the list as shown below.

<em>front        rear </em>




If now we invoke <em>getSmallest</em>(), this will return “id 2” (as this data item has the smallest value) and then the value of <em>front</em> will increase to 2.




You can implement other methods in this class, if you want to, but they must be declared as private.

<h3>2.3 ShortestPath.java</h3>

This class will have an instance variable

<em>CityMap cityMap; </em>

This variable references the object representing the city map where your program will try to find a shortest path, a path with the minimum number of map cells, from the starting cell to the destination cell. Class <em>CityMap</em>, described below, is given to you. You must implement the following methods in this class:

<ul>

 <li><em>public ShortestPath (CityMap theMap).</em> This is the constructor for the class. It receives as input a reference to a <em>CityMap</em> object representing the city map. In this method you must initialize instance variable <em>cityMap</em>: <em>cityMap</em> = <em>theMap</em>.</li>

 <li><em>public void findShortestPath().</em> This method will look for a path with the minimum number of map cells from the starting cell to the destination cell. If a path is found, this method must print a message indicating how many cells there were in the path (including the starting cell and the destination cell). If no path was found, this method must print the message “No path found”. You are encouraged to design your own algorithm to look for a shortest path from the starting cell to the destination. Read the description of the classes <em>Map</em> and <em>MapCell</em> below to see how to select the starting cell and the destination cell, and how to mark cells as visited. If you cannot figure out how to find a path, please read the description of an algorithm given in the next section. <em>private MapCell nextCell(MapCell cell)</em>. The parameter of this method is the current map cell. This method returns the first unmarked neighboring map cell that can be used to continue the path from the current one. Use method <em>isMarked</em> from class <em>MapCell</em> (described below) to determine whether a neighboring map cell has been marked or not. This method is similar to the <em>nextCell</em> method from Assignment 2, except that now we do not prefer the destination or a road intersection cell over the other cells.</li>

</ul>

If there are no unmarked cells adjacent to the current one that can be used to continue the path, this method must return null.

Your program must catch any exceptions that might be thrown. For each exception caught an appropriate message must be printed. The message must explain what caused the exception to be thrown.

You can write more methods in this class, if you want to, but they must be declared as private.

<h1>3. An Algorithm for Computing a Shortest Path</h1>

This section describes an algorithm for computing a shortest path between two map cells. You do not have to implement this algorithm if you do not want to. You are encouraged to design your own algorithm, but the algorithm must use an ordered list from class <em>OrderedCircularArray</em>.

The algorithm starts at the starting cell and as it traverses the map it will store in the ordered list the map cells that it might visit next. Each entry of the circular array will store a <em>CellData</em> object containing

<ul>

 <li>a map cell and</li>

 <li>an integer value equal to the distance from that cell to the starting cell where the Middlesex College building is.</li>

</ul>

As the algorithm looks for a shortest path to the destination cell it will keep track of the distance from the current cell to the destination cell. A description of the algorithm and an example of how the algorithm works are given below.

<ol>

 <li>First, create an empty ordered list using class <em>OrderedCircularArray</em>.</li>

 <li>Get the starting cell where the Middlesex College building is located by using method <em>getStart()</em> from class <em>Map</em>. Each map cell is represented with an object of the class <em>MapCell</em>, described in Section 5.</li>

 <li>Insert the starting cell in the ordered list with a distance value of zero (as the distance from the starting cell to itself is zero). Mark this cell as <em>in the ordered list </em>(use method <em>markInList()</em> from class <em>MapCell</em>).</li>

 <li><strong>While</strong> the list is not empty, <strong>and</strong> the destination cell has not been reached, perform the following steps:

  <ul>

   <li>Remove from the ordered list the map cell <em>S</em> with smallest distance value and mark it as <em>out of the ordered list</em> (to mark the cell use method <em>markOutList</em> from class <em>MapCell</em>).</li>

   <li>If <em>S</em> is the destination cell, then the algorithm exits the while loop.</li>

  </ul></li>

</ol>

Otherwise, the algorithm considers each one of the neighbouring cells of <em>S </em>that

<ul>

 <li>is not null,</li>

 <li>is not a block of houses or a park,</li>

 <li>it has not been marked, and</li>

 <li>it can continue the path from <em>S</em></li>

</ul>

To find these cells you will use your method <em>nextCell</em> described above. For each one of these neighbouring cells <em>C</em> perform the following steps:

<ul>

 <li>Set <em>D</em> = 1 + distance from <em>S</em> to the starting cell.</li>

 <li>If the distance between <em>C</em> and the starting cell (to find this distance use method <em>getDistanceToStart</em> from class <em>MapCell</em>) is larger than <em>D</em> then:</li>

 <li>set the distance of <em>C</em> to the starting cell to <em>D </em>(to do this use method <em>setDistanceToStart</em> from class <em>MapCell</em>).</li>

 <li>Set <em>S</em> as the predecessor of <em>C </em>in the path to the starting cell (use method <em>setPredecessor</em> from class <em>MapCell</em>)<em>; </em>this is necessary to allow the algorithm to reconstruct the path from the initial cell to the destination once the destination has been reached.</li>

 <li>Set <em>P</em> = distance from <em>C</em> to the starting cell.</li>

 <li>If <em>C</em> is marked as <em>in the ordered list</em> and <em>P</em> is smaller than the distance value stored in the entry of the circular array storing <em>C</em> (to find this value use method <em>getValue</em> from class <em>CellData</em>) then use the <em>setValue</em> method from class <em>CellData</em> to update the distance value of <em>C</em> to <em>P</em>.</li>

 <li>If <em>C</em> is not marked as <em>in the ordered list</em>, then add it to the ordered list with distance value equal to <em>P</em>. Then mark <em>C</em> as <em>in the ordered list</em>.</li>

</ul>

<strong>Note</strong>. Recall that you are expected to use meaningful names for your variables when implementing this algorithm. So, do not use <em>C, P</em> and <em>S</em> as names for your variables; use more meaningful names.

To understand how the algorithm works, consider the map given in page 2. The algorithm starts at cell 1 and sets the distance from this cell to the starting cell to 0. Then it examines the neighboring cells; since the east and west neighbors are blocks of houses they are ignored. Cell 3 is added to the ordered list with a distance value of 1 and the predecessor of cell 3 is set to cell 1.

In the next iteration of the while loop, the algorithm removes the map cell 3 from the ordered list. Then two <em>CellData</em> objects are added to the ordered list containing map cells 2 and 4; for each one of these map cells the associated distance value is 2. To understand why the distance value for map cell 2 is 2, note that the shortest path between map cells 2 and 1 is the path 1, 3, 2; this path has length 2 (the distance between 1 and 3 is 1 and the distance between 3 and 2 is 1. Similarly, the shortest path between map cells 4 and 1 is the path 1, 3, 4, which also has length 2.

Next the algorithm removes from the ordered list the <em>CellData</em> object with smallest value, namely cell 4 (because map cells 2 and 4 have the same distance value and map cell 4 was added to the ordered list before map cell 2). From here the algorithm will examine the neighboring unmarked cells of map cell 4, namely 5 and 6. <em>CellData</em> objects storing map cells 5 and 6 are added to the ordered list, each with associated distance value 3; map cell 4 is set as the predecessor of map cells 5 and 6. In the next iteration map cell 2 will be removed from the ordered list.

The algorithm keeps examining cells in this manner until it reaches the destination cell, or it determines that the destination cannot be reached.  When the destination cell is found, the code given to you will automatically highlight in red the path that your algorithm has found.

<h2>4. Command Line Arguments</h2>

The <em>main</em> method is in the provided class <em>CityMap</em>. The program will read the name of the input map file from the command line. From the console you can run the program as follows:

java CityMap name_of_map_file

where name_of_map_file is the name of the file containing the city map. To run the program from Eclipse you need to indicate what the name of the input file is. To do this, in Eclipse select “Run → Run Configurations…”. Make it sure that “Java Application → CityMap” is the active selection on the lefthand side. Select the “Arguments” tab. Enter the name of the file for the map in the “Program arguments” text box. For more details check the tutorial posted in the course’s website:

http://www.csd.uwo.ca/courses/CS1027b/passingParameters.html

<h1>5. Classes Provided</h1>

You can download from the course’s webpage several java classes that allow your program to display the map on the screen. You are encouraged to study the given code to you learn how it works. Below is a description of some of these classes.










<h2>5.1 Class <em>CityMap</em>.java</h2>

This class represents the map of the city including the starting cell and the destination cell. The method that you might use from this class is the following:

o <em>public MapCell getStart().</em> Returns a <em>MapCell</em> object representing the starting cell where the Middlesex College Building is located.




<h2>5.2 Class <em>MapCell</em>.java</h2>

This class represents the cells of the map. Objects of this class are created inside the class <em>CityMap</em> when its constructor reads the map file. The methods that you might use form this class are the following:

<ul>

 <li><em>public MapCell getNeighbour (int i) throws InvalidNeighbourIndexException</em>. As explained above, each cell of the map has up to four neighbouring cells, indexed from 0 to 3. This method returns either a <em>MapCell</em> object representing the <em>i</em>-th neighbor of the current cell or <em>null </em>if such a neighbor does not exist. Remember that if a cell has fewer than 4 neighbouring cells, these neighbouring cells do not necessarily need to appear at consecutive index values. So, it might be for example, that <em>getNeighbour</em>(2) is null, but <em>this.getNeighbour</em>(<em>i</em>) for all other values of <em>i</em> are not null.</li>

</ul>

An <em>InvalidNeighbourIndexException</em> is thrown if the value of the parameter <em>i</em> is negative or larger than 3.

<ul>

 <li><em>public boolean</em> methods: <em>isBlock</em>(), <em>isIntersection</em>(), <em>isNorthRoad</em>(), <em>isEastRoad</em>(), <em>isSouthRoad(),</em> <em>isWestRoad(), isStart(), isDestination</em>(), return true if <em>this</em> <em>MapCell</em> object represents a cell corresponding to a block of houses or a park (where a car cannot drive), a road intersection, a north road, an east road, a south road, a west road, the staring cell where the Middlesex College Building is located, or the destination cell where your house is located, respectively.</li>

 <li><em>public boolean isMarkedInList</em>() returns true if <em>this</em> <em>MapCell</em> object represents a cell that has been marked as <em>in the ordered list</em>.</li>

 <li><em>public boolean isMarkedOutList</em>() returns true if <strong><em>this</em></strong> <em>MapCell</em> object represents a cell that has been marked as <em>out of the ordered list</em>. o <em>public boolean isMarked() </em>returns true if<em> <strong>this</strong> MapCell </em>object represents a map cell that has been marked as <em>in</em> or <em>out of the ordered list</em>.</li>

 <li><em>public void markInList</em>() marks <strong><em>this</em></strong> <em>MapCell</em> object as <em>in the ordered list</em>.</li>

 <li><em>public void markOutList</em>() marks <strong><em>this</em></strong> <em>MapCell</em> object as <em>out of the ordered list</em>.</li>

 <li><em>public int getDistanceToStart</em>()<em>.</em> Returns the distance from the cell represented by <strong><em>this</em></strong> <em>MapCell</em> object to the starting map cell.</li>

 <li><em>public void setDistanceToStart(int dist)</em>. Sets to the specified value <em>dist</em> the distance from the cell represented by <strong><em>this</em></strong> <em>MapCell</em> object to the starting map cell.</li>

 <li><em>public void setPredecessor(MapCell pred). </em>Sets the predecessor of <strong><em>this</em></strong> <em>MapCell</em> object to the specified value.</li>

 <li><em>public Boolean equals(MapCell otherCell).</em> Returns true if <em>otherCell</em> points to <strong><em>this</em></strong> <em>MapCell</em> object, i.e. if <strong>this</strong> object and <em>otherCell</em> have the same address; otherwise it returns false.</li>

</ul>




<h3>5.3 Other Classes Provided</h3>

<em>SortedListADT.java, CellColors.java, CellComponent.java, InvalidNeighbourIndexException.java, CellLayout.java, InvalidMapException.java, IllegalArgumentException.java, EmptyListException, InvalidDataItemException. </em>




<h1>6. Image Files and Sample Input Files Provided</h1>