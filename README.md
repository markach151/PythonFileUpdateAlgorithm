# Algorithm for file updates in Python


## Project description

In this scenario, I am a security professional working at a health care company. I am required to regularly update a file that identifies employees who can access restricted content. The file `"allow_list.txt"` contains the IP addresses linked to employees. There’s also a remove list that identifies which employees I must remove from the allow list. I created an algorithm that uses Python code to check whether the allow list contains any IP addresses identified on the remove list. If so, these IP addresses are removed from the file containing the allow list.   


## Open the file that contains the allow list

For the first part of the algorithm, I opened the `"allow_list.txt"` file. First, I assigned this file name as a string to the `import_file` variable: 

![image6](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/32d9bd6d-8ff1-49d2-9170-68ea3d5205e2)

Then, I used a `with` statement to open the file: 

![image3](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/6a3eff10-a50e-48d3-b211-c785e0ae815e)

In my algorithm, the keyword `with` is used alongside the `open()` function in order to open the allow list file. The keyword `with` will manage external resources by closing the file after exiting the `with` statement. The `open()` function has two parameters: the first identifies the file to import, and then the second indicates what I want to do with the file. In this case, `"r"` indicates that I want to read it. The code also uses the `as` keyword to assign a variable named `file`; `file` stores the output of the `open()` function while I work within the with statement. Now by opening the file I will be able to access the IP addresses stored in the allow list file.  


## Read the file contents

In order to read the file contents, I used the `.read()` method to convert it into a string: 

![image4](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/f0ee2c33-dcfa-42d9-b31d-844ac6509c74)

The `.read()` method converts files into strings. This is necessary in order for me to use and display the contents of the allow list file that was read. I applied the `.read()` method to the `file` variable identified in the `with` statement. Then, I assigned this string to another variable called `ip_addresses`. 


## Convert the string into a list

In order to remove individual IP addresses from the allow list, I needed it to be in list format. Therefore, I next used the `.split()` method to convert the `ip_addresses` string into a list:

![image7](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/9e86cb4c-f5a3-458a-b7e8-ae8879b70b25)

The `.split()` method converts a string into a list. It separates the string based on a specified character that’s passed into `.split()` as an argument. In this algorithm, the `.split()` function takes the data stored in the variable `ip_addresses`, which is a string of IP addresses that are each separated by whitespace, and it converts this string into a list of IP addresses. To store this list, I reassigned it back to the variable `ip_addresses`. The purpose of splitting `ip_addresses` into a list is to make it easier to remove IP addresses from the allow list.  


## Iterate through the remove list

An integral part of my algorithm involves iterating through `remove_list`, which contains all of the IP addresses that should be removed from the `ip_addresses` list. To do this, I incorporated a `for` loop:

![image5](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/7759491c-6cc9-4ed1-9688-4f579e3522eb)

The `for` loop allowed me to automate repetition of the code based on a sequence. The `for` keyword starts the `for` loop. It is followed by the loop variable `element` and the keyword `in`. The keyword `in` indicates to iterate through the sequence `ip_addresses` and assign each value to the loop variable `element`.  


## Remove IP addresses that are on the remove list

My algorithm requires me to remove all of the IP addresses from the allow list (ip_addresses) that are also on the remove list (remove_list). Because there were no duplicates in ip_addresses, I was able to use the following code to do this:  

![image1](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/13744762-a261-445c-8112-d4632993237d)

Within the for loop, I created a conditional statement that evaluated whether or not the loop variable element was found in the ip_addresses list. Applying .remove() to elements that were not found in ip_addresses would result in an error. 

Within the conditional, I applied .remove() to ip_addresses. The variable element was passed in as the argument so that each IP address that was in remove_list would be removed from ip_addresses. 


## Update the file with the revised list of IP addresses 

In the final step of my algorithm, I needed to update the allow list file with the revised list of IP addresses. To do this, I needed to convert the list back into a string. I used the `.join()` method for this:

![image8](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/0f6c8344-792e-40ed-9383-6b08f108d51a)

The `.join()` method concatenates the elements of an iterable into a string. It is applied to a string containing characters that will separate the elements in the iterable once joined into a string. I used the string `("\n")` as the separator to instruct Python to place each element on a new line. In this algorithm, I used the `.join()` method to create a string from the list `ip_addresses` so that I could pass it in as an argument to the `.write()` method when writing to the file `"allow_list.txt"`. 

Then, I used another with statement and the .write() method to update the file:

![image2](https://github.com/markach151/PythonFileUpdateAlgorithm/assets/84886088/e8aa8168-7c25-45a2-9489-cdcdd5acfdad)

This time, I used `"w"` as the second argument in the `open()` function in my with statement. This argument indicates that I want to open a file to write over its contents. When using this argument `"w"`, I can call the `.write()` method in the body of the `with` statement. The `.write()` method writes string data to a specified file and replaces the contents of an existing file.

In this case I wanted to write the updated allow list as a string to the file `"allow_list.txt"`. Now, the restricted content will no longer be accessible to any IP addresses that were removed from the allow list. To rewrite the file, I appended the `.write()` function to the file object `file` that I identified in the `with` statement. I passed in the `ip_addresses` variable as the argument to specify that the contents of the file specified in the `with` statement should be replaced with the data contained in this variable.


## Summary

I created an algorithm that removes IP addresses in a `remove_list` variable from the `"allow_list.txt"` file of permitted IP addresses. This algorithm involved opening a file, converting it into a string to be read, and then converting this string into a list stored in the variable `ip_addresses`. I then iterated through the IP addresses in `remove_list`. With each iteration, I used a conditional statement to evaluate if the element was part of the `ip_addresses` list. If it was, I applied the `.remove()` method to it to remove the element from `ip_addresses`. After this, I used the `.join()` method to convert the `ip_addresses` back into a string so that I could write over the contents of the `"allow_list.txt"` file with the revised list of IP addresses.
