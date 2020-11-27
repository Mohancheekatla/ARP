#                Assignment-1        (5067394,Mohan Cheekatla)
# program composed by two processes using pipe
In this program the user inputs two numbers A and B, random signal is sent through the pipe, every time when a signal is sent it computes the sum  of A and B and increment with respect to last time and the out put is stored in a log file
# installing and running
Machine requires a python 3 installation and the required libraries are pandas,time,datetime,random and string.
script to install required libraries

$ pip3 install pandas && pip3 install time && pip3 install datetime && pip3 install random && pip3 install string

Once the libraries are installed, run the script using $ python3 c1.py

# About the code
Two numbers a&b should be entered by the user and the program generates the random letters, which we are using as signals. After generating of each letter a loop of program excutes and the sum of a&b are incermented.
From P1 sends the data to P2 it should wait for a SIGINT (the signal raised by ctrl-c) to arrive; in that moment it should call a function handler which "listens" to SIGINT and simply sends a signal (eg. SIGCONT) to P2.
All this part inside a loop (which should thus contain simply the pause() used to wait for a signal), since it could be repeated endlessly).
Actually that might even not be necessary, since if P1 is waiting to read something from stdin it's already blocked until an input is given 🤔
So yeah, probably the pause and the loop are not necessary, the definition of a function handler and a scanf are sufficient.
P2 does a similar thing to the first idea, first reads A and B then enters in a loop: inside it it simply sends SIGSTOP to itself, going to sleep until it receives a SIGCONT (which P1 sends), then computes the (a+b)++.
For making it exit when P1 terminates you could use different approaches (like killing it from P1, making a non-blocking read from a pipe where P1 writes when it exits, etc.)
This loop continious until the random letter generates "z" or "Z". And the output log of the program is displayed in shell and stored in a .xlsx file.
