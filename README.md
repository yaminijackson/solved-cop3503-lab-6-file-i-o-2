Download Link: https://assignmentchef.com/product/solved-cop3503-lab-6-file-i-o-2
<br>
<h1>Overview</h1>

For this assignment, you are going to load a series of files containing data and search the loaded data for specific criteria. That might sound a bit dry, but the files contain information about LEGO sets, and everyone loves LEGO! The structure of this assignment is a bit open-ended; you can solve this problem in any way that you see fit.

<h1>Description</h1>

First things first, the files: There are <strong>3</strong> main data files that you will be loading in this assignment:

<ul>

 <li>csv</li>

 <li>csv</li>

 <li>csv</li>

</ul>

The data that you will be loading is information about a LEGO set:

<ol>

 <li>Its set number (really a string, something like: 10195-1)</li>

 <li>The theme it comes from (City, Technic, Star Wars, etc.)</li>

 <li>The name of the set</li>

 <li>How many parts and mini-figures it contains (if any)</li>

 <li>Its price in US dollars</li>

</ol>

Your goal is to read this from 1 of or more of these files, store the data, and then search it based on a few different criteria.

<strong>Main.cpp</strong> is the only file required for this assignment, but you are free to write any class/functions that you see fit to assist you solve this problem. Main.cpp has some structure to it already to help you get started. Take some time to <strong><u>think</u></strong> about the problem, and how you might go about this before diving in.

<h1>Searches</h1>

The different searches you will perform will be based on a menu that might look like this:

<ol>

 <li>Most expensive</li>

 <li>Largest piece count</li>

 <li>Search for set name containing… 4. Search themes…</li>

 <li>Part count information 6. Price information</li>

 <li>Minifigure information</li>

 <li>If you bought one of everything…</li>

</ol>




<table width="623">

 <tbody>

  <tr>

   <td width="312"><strong>Most Expensive </strong><strong> </strong>From the sets that were loaded, which is the most expensive?</td>

   <td width="312">The most expensive set is:Name: Super Awesome Building SetNumber: 99923Theme: CityPrice: $21.99Minifigures: 4Piece count: 286</td>

  </tr>

 </tbody>

</table>




<table width="623">

 <tbody>

  <tr>

   <td width="312"><strong>Largest piece count </strong><strong> </strong>From the sets that were loaded, which has the most parts?</td>

   <td width="312">The set with the highest parts count: Name: Really Big SetNumber: 22231Theme: TechnicPrice: $249.99Minifigures: 0Piece count: 5211</td>

  </tr>

  <tr>

   <td width="312"><strong>Search for set names containing… </strong><strong> </strong>Get a string as input from the user. Then search all sets and their names to see if they contain the search term. There could be a lot of sets matching the search term, so show them in a more concise, list format with the set ID, name, and price. If no sets are found, report that as well.</td>

   <td width="312">Sets matching “Fire Station”: 49281 Fire Station $19.999381 Big Fire Station $49.99 <strong>-OR- </strong><strong> </strong>No sets found matching that search term</td>

  </tr>

  <tr>

   <td width="312"><strong>Search for set themes containing… </strong><strong> </strong>Ditto<a href="#_ftn1" name="_ftnref1"><sup>[1]</sup></a>, but for the theme of the set instead</td>

   <td width="312">Sets matching “City”: 1234 Police Station $29.9949281 Fire Station $19.99// And TONS more… LEGO City is huge! </td>

  </tr>

  <tr>

   <td width="312"><strong>Part count information </strong> Show the average parts for all the loaded sets</td>

   <td width="312">Average part count for 601 sets: 492 </td>

  </tr>

  <tr>

   <td width="312"><strong>Price information </strong><strong> </strong>Show the average, minimum and maximum prices.</td>

   <td width="312">Average price information for 601 sets: $500 Set with the minimum price:[Set data goes here] Set with the maximum price: [Set data goes here]</td>

  </tr>

  <tr>

   <td width="312"><strong> </strong><strong> </strong><strong>Mini-figure information </strong><strong> </strong>Show the average number of minifigures, and the set information for the set with the most minifigures</td>

   <td width="312">Average number of minifigures: 8 Set with the most minifigures:Name: PG2 LectureNumber: COP3503Theme: EducationPrice: $299.99Minifigures: 310Piece count: 938</td>

  </tr>

  <tr>

   <td width="312"><strong>If you bought one of everything… </strong> How much would it costs? How many parts and mini-figures would you have?</td>

   <td width="312">If you bought one of everything… It would cost: $9999.99You would have 200207 pieces in your collection You would have an army of 3000 mini-figures!</td>

  </tr>

 </tbody>

</table>

<h1>Reading Mixed Data From Files</h1>

When reading a text file, oftentimes the data initially gets read in as a string. If the final storage variable isn’t a string (such as a person’s age, or the price of something), you must convert it before storing/using it in its numeric form. In the <strong>&lt;string&gt;</strong> header file, there are a number of functions to help you convert. These function converts a STRING_TO_SOMETHING, and are named like stoi (string to integer), stof (string to float), etc.

Example:

<table width="735">

 <tbody>

  <tr>

   <td width="735">ifstream someFile(“Example.txt”); string someString; someFile &gt;&gt; someString; // We COULD just read directly into the int… but sometimes data doesn’t start out that way. // If you read a lot of data (say an entire line from a file), then you may break // that one string into many smaller strings, and convert as necessary. int convertToInt = stoi(someString);</td>

  </tr>

 </tbody>

</table>

The implementation of some of these functions may throw an exception of type “invalid_argument” if the conversion process fails, so you may want to encapsulate these operations in try/catch blocks, and use a default value if you catch an exception—if the number can’t be converted, (in this case) it’s because a value wasn’t there, so what would be a good value to use in the absence of anything else? Refer back to the section on Exceptions in your textbook if you need to.

<h1>Tips</h1>

<ol>

 <li>Choices you make at the start of a program can have a big impact on how the rest of the program gets developed. Think about how you want to store the information retrieved from the file, and how you could easily pass that data to various functions you might write.</li>

 <li>If you have a process for easily loading and accessing the data, the rest of the functionality should be a lot easier to write. Make sure the loading process is all taken care of before worrying about anything else.</li>

 <li>The code to load 1 file containing 1 piece of data (no matter how complex that data is) should not be much different than loading 100 files, each containing 100 elements. Start by thinking about just 1 element from the file first. Do the values you read match the values in the file? What about 2 entries, does everything add up? Then 3, 4, etc.</li>

 <li>When passing containers of data, make sure you pass them by <strong>REFERENCE</strong>, not by value. Creating copies of massive data sets is generally a bad, bad thing… unless you specifically need to duplicate the data. If not? Then pass by reference (in C++ that means either by pointer or the reference data type)</li>

 <li>There may be a fair amount of repetition in a program like this. Think about where you can create helper functions to reduce the number of times you write the exact same (or just slightly different) code.</li>

</ol>

<strong>         </strong>

<h1>Sample Outputs</h1>

<a href="#_ftnref1" name="_ftn1">[1]</a> A similar thing; a duplicate