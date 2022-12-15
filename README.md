# C-Backdoor

This code is a C backdoor for Windows machines.
It creates a persistent connection that allows a remote user to access and control the device running the code. The code includes functions to execute shell commands, create a registry entry that ensures the code will run when the computer boots, and a keylogger that logs the user's keystrokes. It also hides the console window so the user won't be aware of the malicious activity.

This project consists of three files:

1. backdoor.c

This C code is a Windows system level keylogger that is designed to run in the background and connect to a remote server to send the logged keystrokes. The keylogger is installed and made to run at startup by the bootRun() function. The Shell() function is responsible for handling the connection with the remote server and allows the attacker to execute commands on the victim device. The str_cut() function is used to extract the parameters from the received commands. The WinMain() function is responsible for the initial setup of the keylogger and launching the Shell() function.

2. server.c

This C code is a sample of code used to create a client-server application. The code is setting up a socket connection between a server and a client on the given IP address and port number. The code is setting up the socket with the given IP address, port number, and the socket options. The code is then binding the socket to the server address, listening for a client connection, and accepting the client connection.
Once the client connection is established, the code enters an infinite loop, prompting the user for input and then sending that input to the client through the socket. If the input is "q," the loop is broken and the program terminates. If the input is "cd," the loop is jumped back to the beginning, allowing the user to enter another command. In the case of the "keylog_start" and "persist" commands, the code is receiving a response from the client and then printing it out. In all other cases, the code is receiving the response from the client and printing it out.
Overall, this code is used to establish a socket connection between a server and a client, and then send and receive data through the socket.

3. keylogger.h

This C code is a function logg() which logs keystrokes from the user's keyboard. It does this by creating an array of the last key state of each of the virtual keys (vkey) for the keyboard (0xFF in total). Then, it enters an infinite loop which takes a 10 millisecond rest, gets the state of the CAPSLOCK, NUMLOCK, LEFT_SHIFT and RIGHT_SHIFT keys, and checks the state of all virtual keys.

If the virtual key is pressed (isPressed == 1) and the last state of the virtual key is 0 (last_key_state[vkey] == 0), the key is logged. For example, if the virtual key is between 0x41 and 0x5A, the program checks if CAPSLOCK is 0 and if LEFT_SHIFT/RIGHT_SHIFT is 0. If this is the case, the character is converted to lowercase. If not, it remains in uppercase. The program does similar checks for num chars, right side numpad, printable chars, etc. Finally, the logged key is printed and saved to the file "windows.txt". Lastly, the last state of the key is saved.

This code will run continuously until it is manually stopped, thus allowing the user to log all the keystrokes they make while the function is running.
