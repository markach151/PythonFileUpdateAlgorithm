<!-- Output copied to clipboard! -->

<!-----

Yay, no errors, warnings, or alerts!

Conversion time: 0.684 seconds.


Using this HTML file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Sat Sep 30 2023 11:15:06 GMT-0700 (PDT)
* Source doc: Algorithm for file updates in Python
----->


<h1>Algorithm for file updates in Python</h1>


<h2>Project description</h2>


<p>
As a security professional working at a health care company, I am required to regularly update a file that identifies employees who can access restricted content. The file <code>"allow_list.txt"</code> contains the IP addresses linked to employees. There’s also a remove list that identifies which employees I must remove from the allow list. I created an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list. If so, these IP addresses are removed from the file containing the allow list.   
</p>
<h2>Open the file that contains the allow list</h2>


<p>
For the first part of the algorithm, I opened <code>the "allow_list.txt"</code> file. First, I assigned this file name as a string to the <code>import_file</code> variable:
   
</p>
<p>
Then, I used a <code>with</code> statement to open the file: 
</p>
<p>
In my algorithm, the keyword <code>with</code> is used alongside the <code>open()</code> function in order to open the allow list file. The keyword <code>with</code> will manage external resources by closing the file after exiting the <code>with</code> statement. The <code>open()</code> function has two parameters: the first identifies the file to import, and then the second indicates what I want to do with the file. In this case, <code>"r"</code> indicates that I want to read it. The code also uses the <code>as</code> keyword to assign a variable named <code>file</code>; <code>file</code> stores the output of the <code>open()</code> function while I work within the with statement. Now by opening the file I will be able to access the IP addresses stored in the allow list file.  
</p>
<h2>Read the file contents</h2>


<p>
In order to read the file contents, I used the <code>.read()</code> method to convert it into a string. 
</p>
<p>
The <code>.read()</code> method converts files into strings. This is necessary in order for me to use and display the contents of the allow list file that was read. I applied the <code>.read()</code> method to the <code>file</code> variable identified in the <code>with</code> statement. Then, I assigned this string to another variable called <code>ip_addresses</code>. 
</p>
<h2>Convert the string into a list</h2>


<p>
In order to remove individual IP addresses from the allow list, I needed it to be in list format. Therefore, I next used the <code>.split()</code> method to convert the <code>ip_addresses</code> string into a list:
</p>
<p>
The <code>.split()</code> method converts a string into a list. It separates the string based on a specified character that’s passed into <code>.split()</code> as an argument. In this algorithm, the <code>.split()</code> function takes the data stored in the variable <code>ip_addresses</code>, which is a string of IP addresses that are each separated by whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable <code>ip_addresses</code>. The purpose of splitting <code>ip_addresses</code> into a list is to make it easier to remove IP addresses from the allow list.  
</p>
<h2>Iterate through the remove list</h2>


<p>
An integral part of my algorithm involves iterating through <code>remove_list</code>, which contains all of the IP addresses that should be removed from the <code>ip_addresses</code> list. To do this, I incorporated a <code>for</code> loop:
</p>
<h2>The <code>for</code> loop allowed me to automate repetition of the code based on a sequence. The <code>for</code> keyword starts the <code>for</code> loop. It is followed by the loop variable <code>element</code> and the keyword <code>in</code>. The keyword <code>in</code> indicates to iterate through the sequence <code>ip_addresses</code> and assign each value to the loop variable <code>element</code>.  </h2>


<h2>Remove IP addresses that are on the remove list</h2>


<p>
My algorithm requires me to remove all of the IP addresses from the allow list (ip_addresses) that are also on the remove list (remove_list). Because there were no duplicates in ip_addresses, I was able to use the following code to do this:  
</p>
<p>
Within the for loop, I created a conditional statement that evaluated whether or not the loop variable element was found in the ip_addresses list. Applying .remove() to elements that were not found in ip_addresses would result in an error. 
</p>
<p>
Within the conditional, I applied .remove() to ip_addresses. The variable element was passed in as the argument so that each IP address that was in remove_list would be removed from ip_addresses. 
</p>
<h2>Update the file with the revised list of IP addresses </h2>


<p>
In the final step of my algorithm, I needed to update the allow list file with the revised list of IP addresses. To do this, I needed to convert the list back into a string. I used the <code>.join()</code> method for this:
</p>
<p>
The <code>.join()</code> method concatenates the elements of an iterable into a string. It is applied to a string containing characters that will separate the elements in the iterable once joined into a string. I used the string <code>("\n")</code> as the separator to instruct Python to place each element on a new line. In this algorithm, I used the <code>.join()</code> method to create a string from the list <code>ip_addresses</code> so that I could pass it in as an argument to the <code>.write()</code> method when writing to the file <code>"allow_list.txt"</code>. 
</p>
<p>
Then, I used another with statement and the .write() method to update the file:
</p>
<h2>This time, I used <code>"w"</code> as the second argument in the <code>open()</code> function in my with statement. This argument indicates that I want to open a file to write over its contents. When using this argument <code>"w"</code>, I can call the <code>.write()</code> method in the body of the <code>with</code> statement. The <code>.write()</code> method writes string data to a specified file and replaces the contents of an existing file.</h2>


<p>
In this case I wanted to write the updated allow list as a string to the file <code>"allow_list.txt"</code>. Now, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list. To rewrite the file, I appended the <code>.write()</code> function to the file object <code>file</code> that I identified in the <code>with</code> statement. I passed in the <code>ip_addresses</code> variable as the argument to specify that the contents of the file specified in the <code>with</code> statement should be replaced with the data contained in this variable.
</p>
<h2>Summary</h2>


<p>
I created an algorithm that removes IP addresses in a <code>remove_list</code> variable from the <code>"allow_list.txt"</code> file of permitted IP addresses. This algorithm involved opening a file, converting it into a string to be read, and then converting this string into a list stored in the variable <code>ip_addresses</code>. I then iterated through the IP addresses in <code>remove_list</code>. With each iteration, I used a conditional statement to evaluate if the element was part of the <code>ip_addresses</code> list. If it was, I applied the <code>.remove()</code> method to it to remove the element from <code>ip_addresses</code>. After this, I used the <code>.join()</code> method to convert the <code>ip_addresses</code> back into a string so that I could write over the contents of the <code>"allow_list.txt"</code> file with the revised list of IP addresses. 
</p>
