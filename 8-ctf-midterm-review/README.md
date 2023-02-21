# Midterm Review and CTF challenge

* Pilot submission for today's Capture The Flag (CTF)
* Midterm covers all content in labs/lectures/course repository
* Midterm is ~35 questions, open notes and internet (no communications)
* Any questions?

---

## The CTF

Each table has their own AWS instance (IP Address).  Connect to it with the following:

```bash
ssh -i ./airmanjoe.key airmanjoe@<IP ADDRESS>
```

Once connected you can start hunting for flags!

---

### The flags

Airman Joe has hidden several flags around his Operating System (OS).  Each flag consists of two 
words joined by a symbol.  Examples: 
* `first+second` 
* `flag#staff`
Use the clues to recover them.

##### Hints

* If you get stuck on one challenge skip it and come back.
* Don't forget to check the `man` pages of any of the possible helpful commands!
* Google is your friend, don't be afraid to search for answers.

---

##### Flag 0 - the past

Flag 0 was ran some time in the past, when Airman Joe had a seat at the table, 
protecting the perimeter of his little round table of comrades. 

##### Flag 1 - readme

The first flag is stored in a file called **readme** located in the home 
directory of user airmanjoe: `/home/airmanjoe`.  

You can read it directly if you are already in that directory with `cat readme`,
otherwise you need to specify the whole path to the file like this: 
`cat /home/airmanjoe/readme`

###### Helpful commands

`cat`

---

#### Flag 2- /home sweet /home

The next flag is in a file called **readme** but this file is "up" one directory in `/home`.
I don't care how you get there, just get the flag ;)

###### Helpful commands

`cd, ls, cat, pwd`

---

##### Flag 3 - 

The next flag is stored in a file called **-** located in the home 
directory `/home/airmanjoe`  Easy right? 

###### Helpful commands

`ctrl+c` 

---

##### Flag 4 - space

This flag is stored in a file called **spaces in this filename** in the home 
directory `~/`

###### Helpful commands

`cd, ls, cat`

---

##### Flag 5 - hidden

The flag is stored in a hidden file in the **hidden** directory.
Some helpful hints:

* `pwd` will show you what directory you are currently in
* `cd ../` will change directory one level up
* `cd ~` will go back to your home directory ('/home/airmanjoe')

###### Helpful commands

`cd, ls, man, cat`

---

##### Flag 6 - execute

This flag is output when you run the **execute_me** program in the home directory.
Hint: executing programs from your home directory is a little different, you
need to tell linux *where* the program is...

###### Helpful commands

`cd, ls, cat, ./`

---

##### Flag 7 - It wasn't me...

You will need to use the **setuid** program in your home directory for this challenge.  
The next flag is stored in a file named **readme** in airman **Bob's** home directory 
`/home/airmanbob/readme`.

###### Helpful commands

`whoami, cat`

---

##### Flag 8 - lost

This flag is hidden somewhere in the **lost** directory in a file that is 
exactly 503 bytes.

###### Helpful commands

`cat, find, man`

---

##### Flags 9 & 10 - alike

Two files in the **alike** directory have the same contents.  These two flags
are the names of the two files with identical contents.

###### Helpful commands

`md5sum, diff`

---

##### Flag 11 - Charles in charge

The final flag for today is located in `/home/airmancharles` home directory.  If only you had *permission* to view it.

###### Helpful commands

????

