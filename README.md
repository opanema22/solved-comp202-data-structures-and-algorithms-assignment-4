Download Link: https://assignmentchef.com/product/solved-comp202-data-structures-and-algorithms-assignment-4
<br>
<h1></h1>

This programming assignment will test your knowledge and your implementation abilities of what you have learned in the Maps and Hashmaps parts of the class.

This homework must be completed individually. Discussion about algorithms and data structures are allowed but group work is not. Any academic dishonesty, which includes taking someone else’s code or having another person doing the assignment for you will not be tolerated. <strong>By submitting your assignment, you agree to abide by the Ko¸c University codes of conduct.</strong>

<h2>Description</h2>

This assignment will have two parts. The first part of the assignment requires you to implement hashmaps and related data structures. Specifically, you are asked to implement hashmaps with two different collision checking approaches, a hashmap based counter and a hashset. The second part will require you to solve an applied problem, calculating the co-occurence of words, using the data structures you have implemented. The files you are given include comments to help you out. However, do not hesitate the contact us if anything is unclear.

<h3>Part I: Implementing the Data Structures</h3>

<h4>Hashmaps</h4>

This assignment includes two hashmap versions with different collision handling approaches. One of them uses open addressing, specifically double hashing, and the other uses separate chaining, specifically linkedlists. Both of the approaches use multiply-add-divide (MAD) compression. These hashmaps implement the map interface and extend an abstract hashmap class. This abstract class has some methods and fields, such as the parameters for the compression function, that are common to both implementations. The design of these hashmaps rely on a hashentry class which represent the key-value pairs.

The files provided to you have comments that will help you with your implementation. You can find the files related to hashmap part of the assignment below. Bold ones are the ones you need to modify and they are placed under the <em>code </em>folder, with the rest under <em>given</em>.

<ul>

 <li><em>java</em>: This file defines a simple map interface. Even though you do not need to modify this, make sure to read the comments in detail. It is pretty straight forward. This is the same interface from the binary search tree assignment.</li>

 <li><em>java</em>: This file includes common fields and methods for the hashmaps. The trivial methods are handled for you. The compression function parameters and the method that updates them based on the underlying array capacity are also given to you in this file. You might need to look at this class from time to time while implementing the hashmaps.</li>

 <li><em>java</em>: This file includes the HashEntry class that describes a <em>Key-Value </em>pair for a hashmap. Certain useful methods are implemented for you. This is practically the same as the entry class from the binary search tree assignment. The skeleton of the hashmaps are designed such that the containers hold this type.</li>

 <li><em>java</em>: This file has the base code for the hashmap that uses open addressing for collision handling with double hashing, namely the HashMapDH class. It extends the AbstractHashMap class and implements the iMap interface. Feel free to add more fields and methods. You are not allowed to use existing Java data structures apart from implementing the keySet method. The</li>

</ul>

specific requirements are given as comments just before the class definition.

<ul>

 <li><em>java</em>: This file has the base code for the hashmap that uses separate chaining for collision handling with linked lists, namely the HashMapSC class. It extends the AbstractHashMap class and implements the iMap interface. Feel free to add more fields and methods. You are not allowed to use existing Java data structures apart from the secondary containers and implementing the keySet method. The specific requirements are given as comments just before the class defini-</li>

</ul>

tion.

<h4>Counter</h4>

A counter is an abstract data type that keeps track of how many times equivalent keys are added. It can be considered as a object-integer map with a several modifications. Its main operations are increment (analogous to put) and getCount (analogous to get). Some implementations allow for decrementing the count and/or removing the key altogether which we are not going to need.

In this part of the assignment, you are to implement a counter by wrapping a hashmap. The counter will hold an internal hashmap (instead of extending it) which can be supplied from the outside. The class is setup such that you are only going to fill two methods, rest are handled for you. Make sure you understand the requirements of the increment and the getCount methods from the comments!

The only file that you need to work on for this part is the <em>HashCounter.java </em>file under the <em>code </em>folder.

<h4>Set</h4>

A set is an abstract data type that holds unique keys without any particular order. It can be considered as an implementation of the mathematical finite set concept. Its main operations are put, remove and contains which should be self-explanatory. Sets can be implemented by binary search trees or as hashsets. Set data structure does not involve key-value pairs but only involve keys. During the class, most of our examples for maps only had a key instead of a key-value pair so this part should not pose any difficulty.

In this part of the assignment, you are to implement a set using hashing ideas. You can directly use one of your hashmap implementations and hide the value or you can implement a hashset from scratch. The former is easier, the latter will end up cleaner and faster. The files in this part of the assignment are below. Bold ones are the ones you need to modify and they are placed under the <em>code </em>folder, with the rest under <em>given</em>.

<ul>

 <li><em>java</em>: This file defines a simple set interface. Even though you do not need to modify this, make sure you read the comments in detail. It has some differences with the map interface but it is still pretty straight forward.</li>

 <li><em>java</em>: This file contains the fairly empty definition of the HashSet class which extends the set interface. You are free to design and implement it however you want. However, you are not allowed to use existing Java data structures apart from the secondary containers and implementing the keySet method.</li>

</ul>

<h3>Part II: Word Co-Occurrence Calculation</h3>

In fields related to computational linguistics, it is common to assume that semantically related terms appear together wihin a context. These terms are usually taken as words, which define the concept of <em>word co-occurrence</em>. The context can differ, from single sentences to entire documents.

In this part of the assignment you are going to count the number of times two words appear together within a certain distance of each other in a single sentence given some text. You are going to form a <em>word co-occurrence matrix</em>. This is a square matrix where row and column indices correspond to words and the specific entry in a given coordinate correspond to number of times that these two words occur together.

Suppose we are given the text “To be or not to be. That is the question.” and are asked to compute the co-occurence matrix. The context is given as 2 neighboring two words in a sentence:

<ol>

 <li>The first step we are going to take is about finding the unique words (this does not need to be a separate step but helps the example). The set of unique words is {to,be,or,not,that,is,the,question}. It is common practice to convert all to lower case.</li>

 <li>The second step is to separate the sentences which is trivial. The list of sentences is [to be or not to be, that is the question].</li>

 <li>The third step is to iterate over these sentences. For each word, we find its neighbors within the given distance and jointly count them. For example:

  <ul>

   <li>For the first “to” in the first sentence, its neighbors are “be” and “or”. We set the entries that correspond to to-be and to-or to 1</li>

   <li>For the first “be”, the neighbors are “to”, “or” and “not”. We set the entries that correspond to be-to, be-or and be-not to 1</li>

   <li>For “or”, the neighbors are “to”, “be”, “not” and “be”. The entries should be set accordingly.</li>

   <li>Skipping to the second “to”, the neighbors are “or”, “not” and “be”. We have seen to-be and to-or before so we incement them to 2 and set to-not to 1.</li>

  </ul></li>

</ol>

Note that we do not count any neighbors outside the sentence. If we do it for all the words and sentences we get the following word co-occurence matrix:

<table width="601">

 <tbody>

  <tr>

   <td width="67"> </td>

   <td width="67">to</td>

   <td width="67">be</td>

   <td width="67">or</td>

   <td width="67">not</td>

   <td width="67">that</td>

   <td width="67">is</td>

   <td width="67">the</td>

   <td width="67">question</td>

  </tr>

  <tr>

   <td width="67">to</td>

   <td width="67">0</td>

   <td width="67">2</td>

   <td width="67">2</td>

   <td width="67">1</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

  </tr>

  <tr>

   <td width="67">be</td>

   <td width="67">2</td>

   <td width="67">0</td>

   <td width="67">1</td>

   <td width="67">2</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

  </tr>

  <tr>

   <td width="67">or</td>

   <td width="67">2</td>

   <td width="67">1</td>

   <td width="67">0</td>

   <td width="67">1</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

  </tr>

  <tr>

   <td width="67">not</td>

   <td width="67">1</td>

   <td width="67">2</td>

   <td width="67">1</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

  </tr>

  <tr>

   <td width="67">that</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">1</td>

   <td width="67">1</td>

   <td width="67">0</td>

  </tr>

  <tr>

   <td width="67">is</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">1</td>

   <td width="67">0</td>

   <td width="67">1</td>

   <td width="67">1</td>

  </tr>

  <tr>

   <td width="67">the</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">1</td>

   <td width="67">1</td>

   <td width="67">0</td>

   <td width="67">1</td>

  </tr>

  <tr>

   <td width="67">question</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">0</td>

   <td width="67">1</td>

   <td width="67">1</td>

   <td width="67">0</td>

  </tr>

 </tbody>

</table>

Note that the matrix is symmetric. Co-occurrence matrices in general do not need to be symmetric but our definition of the context made it so.

For certain problems, it is desirable to ignore certain extremely common words such as the English articles “a”, “an”and “the”. Another, potentially harmful, approach is to ignore words that are shorther than two characters since they maybe one of the common words.

For other problems, there is only a set of keywords that we care about and want to calculate the co-occurence matrix just based on those, ignoring all the words.

The file <em>HashBasedWordCo.java</em>, has the skeleton of the code to implement this part. This class takes an entire text as a string and calculates the co-occurence matrix. The matrix is represented by a hashmap of string – hashcounter of string. A lot of support code such as loading files, pre-processing text and splitting the sentences are done for you. You should go over them. You need to complete two methods; (1) finding the unique words and (2) calculating the matrix. You may use anything you have implemented in this assignment but not allowed to use any other Java data structures apart from the given sentence lists. In fact, the class uses your implementation of hashmaps, hashcounters and hashsets.

Note that you are given two printing functions, one to the console and the other to a csv file, to help debug your code.

<h3>Warnings</h3>

All the methods that take a key as input should return null if the key is null. If the method return type is a primitive, it should return -1 if numeric and false if boolean. There are not any other options for this assignment.

Read all the comments, they are helpful. Let us know if they are confusing, contradictory or unclear. This assignment, especially the last part might seem to be difficult but everything is given either in this document or in the comments.

You are not allowed to use any default Java data structures other than to implement the keySet methods and for the secondary containers of the HashMapSC class. The <em>HashBasedWordCO.java </em>file has lists and arraylists for limited parts which you can use but do not add your own.

<ul>

 <li></li>

</ul>