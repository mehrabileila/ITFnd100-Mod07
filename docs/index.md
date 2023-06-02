**Title:** *Introducing  Binary Files and  Structured Error Handling (Try-Except) in Python*  
**Dev:** *Leila Mehrabi*  
**Date:** *01/06/2023*  
# Introduction    
This lesson taught us about working with binary files and Python’s error-handling method. We’ll explain these two concepts in more detail in the following sections.  
# Error Handling (Try-Except)  
Try-Except block of code is an easy way of handling errors that usually happen when users run the program. This block of code allows us to customize the error message instead of letting Python show its own error message, which is often not very user-friendly, especially for non-technical users. Three blocks of code can handle the structural errors when we run them together. These are four blocks: 
-The try block lets you test a block of code for errors.
-The except block lets you handle the error.
-The else block lets you execute code when there is no error.
-The finally block lets you execute code, regardless of the result of the try- and except blocks.  
Example:  
The try block will generate an exception because x is not defined: (https://www.w3schools.com/python/python_try_except.asp)   
![The Try Block Example]( https://github.com/mehrabileila/ITFnd100-Mod07/blob/main/docs/Picture1.png "Figure1: The Try Block Example")   
**Figure1: The Try block example**    
## Code Details for Try_Except block  
The program starts and tries to open a text file and read the content. If the file doesn’t exist, an exception of type  FileNotFoundError is raised, and the program exits.  
```   
try:
    print("Trying to open the file 'Leila.txt'...")
    fileobj = open("Leila.txt", "r")

except FileNotFoundError as e: # If file doesn't exist throws an exception
    print("Text file must exist before running this script! Please create a file named 'Leila.txt'")
    print("Built-In Python error info: ")
    print(e, e.__doc__, type(e), sep='\n')   
```   
**Listing 1: Try-Except block example**   
  
If the file exists and there is no exception, then the program continues to open and read the file. So in this program, we are using a combination of try, except, and else.  
```  
try:
    print("Trying to open the file 'Leila.txt'...")
    fileobj = open("Leila.txt", "r")

except FileNotFoundError as e: # If file doesn't exist throws an exception
    print("Text file must exist before running this script! Please create a file named 'Leila.txt'")
    print("Built-In Python error info: ")
    print(e, e.__doc__, type(e), sep='\n')
else: #If file exists then the program continues to open and read it
    fileobjData = fileobj.read()
    print("Current data in the file: ")
    print(fileobjData)
    fileobj.close()  
```  
**Listing 2: Try-Except-Else block**   
  
Then the program continues to read new numbers from the user. If the number is between 1 and 5, it is accepted and stored in the file. If not, another exception is raised, and the user is informed that the number is not in range.  
![Exception raised to inform the user that the number is not between 1 and 5]( https://github.com/mehrabileila/ITFnd100-Mod07/blob/main/docs/Picture2.png "Figure2: Exception raised to inform the user that the number is not between 1 and 5")  
**Figure 2: Exception raised to inform the user that the number is not between 1 and 5**    
  
# Working with Binary files in Python  
Working with binary files in Python is called pickling. Python pickle module is used for serializing and de-serializing a Python object structure. Any object in Python can be pickled so that it can be saved on disk. What Pickle does is it “serializes” the object first before writing it to a file. Pickling is a way to convert a Python object (list, dict, etc.) into a character stream. The idea is that this character stream contains all the information necessary to reconstruct the object in another Python script. ( https://www.geeksforgeeks.org/understanding-python-pickling-example/)  
## Pickling Code Detail  
The code example for pickling is a simple program that asks for the name and email address and then saves them to a binary file. The program can then display the binary file data per the user’s choice. This program uses functions ‘load’ and ‘dump’ from module ‘pickle’ to read from and write into the file. If the user chooses 2, the program displays the current data by opening the file in “rb” (read/binary) mode. Then the program loads the data into a list and finally displays the list.  
```  
elif(strchoice=="2"):# display current data in binary file
      try:
        with open("Leila.dat", "rb") as f:
              while True:
                  try:
                      objfileDataLst2.append(pickle.load(f))
                  except EOFError:
                      break
              print(objfileDataLst2)
              f.close()
      except FileNotFoundError as e:
          print("Text file must exist before we can display the current data! Please create a file named 'Leila.dat'")
          print("Built-In Python error info: ")
          print(e, e.__doc__, type(e), sep='\n')  
 ```  
 **Listing 3: The code to display binary file data**  
   
 If the user chooses 1, the program captures the data ( name and email address) from the user and stores them in the binary file.  
 ```  
   elif (strchoice=="1"):#add new data to binary file
     strname=input("Enter your name: ")
     strEmail=input("Enter email address: ")
     lstrecord=[strname,strEmail]
     objfile2=open("Leila.dat","ab")
     pickle.dump(lstrecord,objfile2)
     objfile2.close
     continue  
 ```  
 **Listing 4: The code to save data to the binary file**     
  
 ![Running the program in Windows command prompt]( https://github.com/mehrabileila/ITFnd100-Mod07/blob/main/docs/Picture5.png "Figure3: Running the program in Windows command prompt")  
 **Figure 3: Running the program in Windows command prompt**  
   
![Running the program in PyCharm]( https://github.com/mehrabileila/ITFnd100-Mod07/blob/main/docs/Picture6.png "Figure4: Running the program in PyCharm")  
 **Figure 4: Running the program in PyCharm**   
 # Summary  
 In this assignment, we learned how to work with binary files, read and write data to them. We also learned how to handle structural errors in Python using the Try-Except block.  
 
 
