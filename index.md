# Learning to Code C++ Part 4

## *Table of Contents*
**Storage and Linked Data**  

1.  Types of Memory  
	* Speed
	* Buffering/Memory Flow
2. Workflow  
3. fread and fwrite
4. 

---

## Types of Memory

### Hard Drive
The hard drive is much slower to read than RAM  
Reading and writing to the hard drive is inevitable  

* File IO  
* Data Bases  

Whenever we hit the hard drive the Program is going to slow down  
* Even some modern SSD's are quite slow

### Speed?
So can we speed this up?  
We know RAM is quicker  

* We can exploit RAM to make the hard drive operations quicker

This is where **buffering** comes in

### Buffering
This is used to make reading and writing to the HD a lot quicker  
Certain languages such as Java do this for us under the correct circumstances  

* BufferedInputSteam / outputStream

The idea here is that we are going to create a buffer in RAM that holds information from the hard disk  
That buffer will be our "middle manager" allowing us to limit how much we use the drive  

When we want to use the drive we will read larger chunks of data in one operation into an Array in RAM  


## Workflow
The workflow for the algorithms is the same  
Writing:  
* Create the buffer  

	* Fill it with information  
* When the buffer is full, write the information to the disk  


* Empty the buffer and start again

Reading:  

* Create the buffer  
* Read a chunk of file
* Process through it
* Get more from the file

## fread and fwrite
These two are found in #include\<stdio.h>  
They are how we work with binary byte data in C/C++ file I/O  
Like fscanf/fprintf we need a file pointer to work with here  
`<bytes read> = fread(<buffer>, sizeof(<buffer>), <# of items to read of 2nd param>, <file pointer>);`

`char buffer[100];`  
`File *filepointer;`  
`int bytes = fread(buffer, sizeof(buffer), 1, fp);`

### Syntax Differences


A buffer s loaded with bytes of that information  
The second parameter indicated the size of the things stores in the byte array memory  
The third parameter indicates how many of those things should be read or written  

This means that you can load up that byte array with binary patterns of data and read/write it into our records  

* Great for outputting whole records, compressed data, encrypted data and serialization



## fseek
This allows us to manipulate the file pointer directly  

* Allows for movement of the file pointer in the file itself

Syntax:   
`fseek (<file pointer>, <bytes to move>, <from where?>);`  

The \<from where> portion is constant that tells the command how to act

*  SEEK_SET - From the beginning of the file  
*  SEEK_CUR - From the current location of the file pointer
*  SEEK_END - From the end of the file

This command in conjunction with others allow you to structure your files and retrieve things algorithmically  

* File Structures 
