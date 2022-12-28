# Operating-Systems
server-client-signal:
This code is a server program in C that performs arithmetic operations on two numbers received from a client.
The server listens for a signal from the client, and when it receives the signal, it reads the client's request from a file called to_srv.txt.
The request consists of the client's process ID (pid), the two numbers to be operated on, and the operator (+, -, *, or /).

The server then forks a child process to perform the requested operation, and sends the result back to the client by writing it to a file called to_cli.txt.
If the client's request is invalid (e.g., if the operator is not recognized or if the client tries to divide by zero), 
the server sends an error message to the client instead of a result.

The serverHandler function is called when the server receives a signal from the client. 
It reads the client's request from to_srv.txt and stores it in an array of strings called arg. 
It then forks a child process and calls the calculate function in the child. 
The calculate function parses the arg array, performs the requested operation, and writes the result to to_cli.txt. 
If the operation is invalid, it writes an error message to to_cli.txt instead.

The itoa and reverse functions are used to convert an integer to a string and reverse the string, respectively. 
The getSize function is used to determine the length of a line in to_srv.txt.



fork:
This code is for a program that is supposed to run multiple student programs and compare their outputs with expected outputs. 
The program does the following:

Reads a list of student programs and their arguments from a file, and for each student program it:
Forks a child process to run the student program and write its output to a file "outPro.txt".
Forks another child process to run a program called "part1.exe" which compares "outPro.txt" with an expected output file,
and returns 0 if they are equal and 1 if they are not.
Forks a third child process to write the student's name and the result (either 100 or 0) to a results file.
The main function reads the list of student programs and arguments from a file called "input.txt",
and passes them to the checkGrade function along with the expected output file and the file descriptor for the results file.
The checkGrade function then uses fork() to create the child processes and execvp() to execute the student programs and part1.exe.

The code also includes a function called getSize() which gets the size of a line in a file by reading it character by character
until it reaches a null character or a newline. This function is used to determine the size of each line in the input file so that the correct 
amount of memory can be allocated for the arrays that will store the student program paths and arguments.




