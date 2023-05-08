Download Link: https://assignmentchef.com/product/solved-project-1-linked-list-solution
<br>
<h2>Introduction – The Problem</h2>

In this project your program demonstrates two applications of the linked list based sequence ADT. The first stores Rectangle objects, the second stores String objects. Your program must test all the sequence operations at least in one of the two data structures created. The rectangle objects are created and added to the list with random field values, the string objects (names) you choose directly or read them from a file you create for input, or you may generate names randomly, too. Must document your choice.

<h2> Design, Implementation</h2>

The implementation of the data structure ADT will be based on two user defined classes:<strong> Node </strong>and<strong> LinkedSequence</strong>, both generic. A <strong>Rectangle</strong> class must

also be added to project, since in one of the applications the stored data are Rectangle objects. The other application utilizes the String class from the Java library. For testing purposes two more classes will be needed: <strong>TestNode</strong> to test the Node class methods, and <strong>LinkedApplications</strong> to use the data structure.

<ol>

 <li>The <strong>Rectangle</strong> class (not generic) has two fields named <strong>width</strong> and <strong>length,</strong> both of type <strong>int. </strong>You may use package access to the fields. The class has</li>

</ol>

<ul>

 <li>a constructor taking two parameters to initialize the fields</li>

 <li>a toString( ) method which returns a String message that specifies the data field values</li>

 <li>an equals( ) method which returns true if each of the corresponding field values are equal in two given rectangles</li>

</ul>

<h2>2. Node</h2>

This class is <strong>generic</strong>, yet as for a template, you are advised to study the IntNodeClass specifications (pp 208-211, Figure 4.11 in Ch 4) in the book, as well as the implementations in the previous sections and on pages 212-214. As for a generic Node class there are some hints in the book on pages 283-285 (Sec 5.4 in Ch 5).

Our <strong>Node</strong> class is similar but not identical to the template. We may discard or modify some methods and we may include new methods which are practical in our applications.




<strong> Partial class documentation</strong>:




<ul>

 <li><u>Fields</u>: as usual, but with the generic type parameter</li>

 <li>Constructor: takes two parameters to initialize the fields</li>

</ul>




<h3>Instance methods</h3>

<ul>

 <li><strong>addNodeAfter()</strong> as in the book, but <strong>not void</strong>, returns the link it creates.</li>

 <li><strong>removeNodeAfter()</strong> as in the book, but returns the link it creates (that is, the node after the removed element)</li>

 <li><strong>toString()</strong> creates and returns a string message which reveals the stored value (data) but not the link (this method is not recursive, it overrides Object toString)</li>

 <li><strong>toString(int dum)</strong> creates and returns a string message which reveals the stored value (data) and the links (recursive). This method overloads toString, this is why a dummy parameter is needed. The method is applicable for shorter lists only, needed for testing purposes and not supposed to be in a reusable class. See HW 4 discussing both the recursive and non-recursive versions of toString().</li>

</ul>

<strong> </strong>

<h3>Static methods</h3>

<ul>

 <li><strong>listCopy()</strong> as in the book, but, since our addNodeAfter( ) returns the link, you should assign the return value directly to copyTail . That is, combine the two copyTail statements of the while loop in one statement, see the slide from the lecture.</li>

 <li><strong>listPosition()</strong> as in the book</li>

 <li><strong>listLength()</strong>as in the book</li>

 <li><strong>getTail() This is a new method! </strong>Starting at a node given as</li>

</ul>

the parameter, the method iterates through the list until arrives at the tail, then it returns the tail. The iteration is the same as in the listCopy method. This method helps to maintain the tail reference, and combined with the listCopy method, the listCopyWithTail becomes superfluous

<ul>

 <li><strong>listCopyWithTail() </strong>omitted</li>

 <li><strong>listPart()</strong> omitted</li>

 <li><strong>listSearch()</strong>omitted</li>

</ul>

<h2>3.  LinkedSequence</h2>

This class is also implemented as a <strong>generic</strong> class. The specification of a nongeneric DoubleLinkedSeq class is fairly well detailed in your reading, pp 232 – 238, it helps to design the generic class. It is a marked difference that the book does not apply a dummy node. Also, the LinkedBag implementation in the book can be helpful, but the analogy is rather weak.




<strong><u>Fields</u> </strong>

<ul>

 <li>The field manyNodes is optional.</li>

</ul>

It can be convenient to have direct access to the size of the sequence, but this variable needs careful update in each method that manipulates the size, and this can be a source of errors. For instance, the removeNodeAfter() method changes the size most of the time, but there is no change when tail is the reference. The listLength() method of the Node class makes the field dispensable, but the length algorithm is O(n).




There are five private variables of type Node:

<ul>

 <li>head</li>

 <li>tail</li>

 <li>cursor</li>

 <li>precursor</li>

 <li>dummy</li>

</ul>

<h2>                            <u>The </u><u>LinkedSequence</u><u> invariant</u></h2>

For your convenience the <strong>invariant </strong>as part of the class documentation is supplied. When you design and implement the methods, it is important that you pay attention to the invariant.




<ol>

 <li><strong>manyNodes</strong> is the number of nodes in the sequence; in particular the value is <strong>0</strong> for an empty sequence</li>

 <li>For a non-empty sequence <strong>head</strong> is the reference to the first, and <strong>tail</strong> is a reference to the last node of the sequence; for an empty sequence <strong>head</strong> and <strong>tail </strong>are null</li>

 <li>For a non-empty sequence <strong>cursor</strong> can be a reference to any of the nodes of the sequence, it cannot reference <strong>dummy</strong>. The <strong>cursor</strong> can be null; for an empty sequence <strong>cursor</strong> is null</li>

 <li>If <strong>cursor</strong> is not null, <strong>precursor</strong> is a reference to a node such that <strong>cursor</strong> is <strong>link</strong>. If <strong>cursor</strong> is null, <strong>precursor</strong> is null; in particular <strong>precursor</strong> does not reference <strong>tail</strong></li>

 <li><strong>dummy</strong> is a node reference and it is never null (dummy is not an element of the sequence); <strong>link </strong>is always head (null or not). If <strong>cursor</strong> is the <strong>head</strong>, then <strong>precursor</strong> is <strong>dummy</strong></li>

</ol>




<strong>            <u>Methods and Constructors</u> </strong>




All the fields except dummy require accessor and mutator methods.

You should instantiate dummy at the declaration with two null parameters.




<h3>                            Constructor</h3>

 Takes one node parameter to initialize the head. To initialize tail, head is assigned. Assigns dummy’s link the head (setLink() must be used). Note that dummy does not store any info data but null, and it is not part of the data structure. Its link is always the head, see that ADT invariant.

<h3>                        Instance Methods</h3>

<strong> </strong>

<ul>

 <li><strong>addAfter</strong>( ) Takes a parameter for the new <strong>data </strong>value to be added to the structure and returns the currently added node. Cursor reference is always updated to the added node. A call to the addNodeAfter method of the Node class shall add the new node to the list

  <ul>

   <li>after dummy if head is null</li>

   <li>after tail if cursor is null but head is not</li>

   <li>after cursor if cursor is not null</li>

  </ul></li>

</ul>




Build the selection logic carefully and update the relevant fields as necessary




<ul>

 <li><strong>addBefore</strong>( ) Takes a parameter for the new <strong>data</strong> value to be stored in the structure and returns the currently added node. Cursor reference is always updated to the added node. A call to the addNodeAfter method of the Node class shall add the new node to the list

  <ul>

   <li>after dummy if precursor is null</li>

  </ul></li>

</ul>

<strong>(ii)</strong>after precursor if precursor is not null




<ul>

 <li><strong>addAll( )</strong>Takes another linked sequence for parameter (‘<strong>other</strong>’) and joins the parameter list to this list after this tail. If the parameter is null or empty, the method returns. Otherwise, if the calling list is empty (head is</li>

</ul>

null) this head assigned other head and this tail assigned other tail; else tail link assigned other head and tail assigned other tail.




<ul>

 <li><strong>advance()</strong> advances the cursor forward one step, if the cursor is not null and not the tail; precursor is updated accordingly. Null cursor is advanced to head, tail cursor advanced to null.</li>

</ul>




<ul>

 <li><strong>start() </strong>if the sequence is empty, the method returns; otherwise assigns cursor the head and precursor the dummy</li>

</ul>

<strong> </strong>

<ul>

 <li><strong>clone( )</strong> Returns a copy of the calling sequence. See the specifications in the book.</li>

</ul>




<ul>

 <li><strong>concatenate( )</strong> static method; takes two linked sequence parameters and creates a third sequence by adding the second after the first. You have to use the listCopy( ) and getTail( ) static methods from Node. <strong>Do not use</strong> listCopyWithTail( ).</li>

</ul>




<ul>

 <li><strong>removeCurrent()</strong> removes the cursor if cursor is not null and returns the removed node. The new cursor is the following node if there is one, and precursor updated accordingly. If tail was removed, the new new cursor is head if there is head, if so precursor is dummy. If cursor is null, the method returns null.</li>

</ul>




<ul>

 <li><strong>displayList( )</strong> convenience method. Prints all the nodes to the console; use the toString( ) call with respect to head for the recursive version and run a loop for the non-recursive version.</li>

</ul>




<h3><strong>4.</strong> <strong>TestNode </strong></h3>

Create three-node long list(s) of String type and test all the Node methods. This part of the Project is an extension of HW 4, you may use your code from that assignment.

<h3><strong>5.</strong> <strong>LinkedApplications </strong></h3>

<h4>Requirements</h4>

<ul>

 <li>Create short (three to five long) String type linked list to test all the methods.</li>

 <li>The displayList( ) method must be tested on Rectangle type list</li>

 <li>Add two <strong>static</strong> fields of type <strong>long</strong> to the application class named <strong>squares </strong>and <strong>occurrences</strong></li>

 <li>Add a static void method named <strong>counting</strong> to the applications class. The method takes a Rectangle array named boxes and a Rectangle object named target for parameters.</li>

 <li>The method counts the number of squares among the array element, and stores the value in the <strong>squares</strong> field, and it also counts the number of array elements that are equal to the target and stores the result in the <strong>occurrences</strong></li>

 <li>Step 1: Create a LinkedSequence of 100 000 Rectangle objects each having integer dimensions randomly selected between 1 and 30.</li>

 <li>Step 2: Verify that the listPosition() method returns the tail reference for position number 100 000.</li>

 <li>Step 3: instantiate a Rectangle array to the list length (do not use literals) and load the Rectangles from the list to the array.</li>

 <li>Step 4: Create a target Rectangle with side 15, 15 and call the counting method passing your array and target as parameters.</li>

 <li>Step 5: Measure the running time of each step above as well as the combined time and record the results. Hint: use the method call <strong>nanoTime() </strong>to record the current real time in nanoseconds (the return type of the method is <strong>long</strong>); note that<strong> 10<sup>9</sup> </strong>nanos make one second.  Step 6: Repeat Steps 1- 5 for 1 000 000 Rectangle objects  Step 7: Repeat Steps 1 – 5. 10 000 000 Rectangle objects.</li>

 <li>Step 8: Repeat Step 7 by adding the non-random target rectangle of step 4 to the empty list 10 000 000 times. Check out if the random selection in step 7 is a significant overhead for the running time of the algorithm or not.</li>

 <li>Analyze your running time observations, deduce Big-Oh estimates and advise about the expected time for the case of 100 000 000 rectangles. Attach your report as a comment to the source code following the application class.</li>

</ul>

<strong><u>Documentation</u></strong>:  Each method in Node and LinkedSequence must be fully documented (specification). You may use the assignment description itself as a help to compile the specifications.


