# OverTheWire Bandit
## Welcome!
Welcome to the OverTheWire Bandit writeup! Bandit is one of a series of wargames produced by OverTheWire and can be found at https://overthewire.org/wargames/bandit/. It is designed with beginners in mind, so if you have little to no experience using a terminal, this is the place for you! 

![image](https://github.com/massey-n/CTF-Writeups/assets/136398242/584f7373-0749-4212-8dc7-b9de4adb22e9)

Both Bandit and this writeup are written with the assumption that you are using a Linux machine. I recommend Kali Linux if you have an interest in cybersecurity, but there are tons of distros out there for you to choose from.

I will walk through my process for each level and explain any core concepts and commands that are useful. I would strongly recommend trying each level on your own, and once you've completed it or gotten stuck, check the writeup to see if you missed anything. My goal isn't to do this **for** you, it's to show you how I approached things and fill in any gaps.

Enough talk, let's get right into it! Hit the link to Bandit 0 and dive right in!

## Level 0

![image](https://github.com/massey-n/CTF-Writeups/assets/136398242/949d572f-a249-4398-b125-db9c8742d685)

### Concepts:
[ssh, man]
Ssh stands for **S**ecure **Sh**ell, and serves as a means to connect remotely to a server or device. The basic syntax for this command is ```ssh [username]@[host]```. 

The instructions state that we need to connect to a specific port, which is not covered in the basic syntax. To find out more about nearly any command, simply type:
```man [command]``` This shows the manual for the command, which includes *switches*, or options, that can focus the command.

This is the man page for ssh:



Scroll through a bit, and keep an eye out for anything mentioning a port. You'll find that -p should suit our purposes nicely. 

### Solution:
Using what we've learned, type out the following command, using the given information:

```ssh bandit0@bandit.labs.overthewire.org -p 2220```

You'll be prompted to enter a password, which is also given. Once you do, you're in! 

![image](https://github.com/massey-n/CTF-Writeups/assets/136398242/d1cf77d1-34f7-4a25-adc1-fe88e5804ea6)

## Level 0 --> Level 1

![image](https://github.com/massey-n/CTF-Writeups/assets/136398242/eb1a2671-6ccb-4077-a7fa-b456af7f6c7b)

### Concepts:
[ls, cat]
ls is a command that is used to list the files found in the current directory. The syntax is simple, just enter ls followed by any switches: ```ls [options]```.

cat is another command, used to show to contents of a file. The syntax is equally simple: ```cat [file_name]

### Solution:

This one's pretty simple, just use ```ls``` to confirm the file is here, then use ```cat readme``` to show the password.

You'll want to keep these somewhere, in case you take a break or lose connection somehow. It's much easier than redoing all the levels!
To copy it, just highlight it and use ```CTRL+shift+C```.

![image](https://github.com/massey-n/CTF-Writeups/assets/136398242/9f4bb798-502f-4178-8fed-d021c779b44f)

## Level 1 --> Level 2

![image](https://github.com/massey-n/CTF-Writeups/assets/136398242/b6c9c5d5-8df4-4940-ba4c-b5696404f74d)

### Concepts:
[Directories, paths]

A directory is a storage place for files. Folders on a Windows system are directories. 

A *path* is the string of directories that leads to a file or directory. The path to the bandit1's home directory is: ```/home/bandit1```. (This can be seen by using the command pwd, which stands for print working directory)

The characters .  ..  ~  / each represent a certain directory. "." refers to the current directory. ".." refers to the parent directory, meaning the one that came before it. "~" refers to the user's home directory. "/" at the beginning of a path refers to the root directory.

Switches make use of dashes "-" to let the command identify them. As such, the shell reads the dash as the start of a switch. That poses a problem if a file starts with a dash!

### Solution:

Log in to bandit1 via ssh, using the password we just got. Run ls to make sure we're in the right spot.

If you try ```cat -```, the terminal will hang as it tries to figure out what you mean (break out of this with CTRL+C). Taking what we just learned about directories, how do you think we can distinguish "-" as a filename rather than a switch?

The character "." means the current directory. As such, ./filename and filename mean the same thing. Try this with the dashed file and you'll have solved this level!

![image](https://github.com/massey-n/CTF-Writeups/assets/136398242/caef7f46-c9ad-43ef-a0b9-c242a7edb104)
