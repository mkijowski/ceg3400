# CTF Network Exercise

Again you will need Airman Joe's private key:

```bash
wget https://raw.githubusercontent.com/mkijowski/ceg3400/refs/heads/master/08-ctf-midterm-review/airmanjoe.key
```

Use the above key ***with the correct permissions*** to sign into your table's server IP.

```bash
ssh -i airmanjoe.key airmanjoe@<IP ADDRESS>
```

---

### The flags

Airman Joe has found out that the administrator of his home directory (on another system) has hidden several flags, ***each on a different network port*** on a remote system on the **local network**.  Each flag consists of two words joined by a symbol.  Examples: 
* `first+second` 
* `flag#staff`
Use the clues to recover them.

#### Hints

* Most ports will only allow one person at a time, ***communicate***
* If you get stuck on one challenge skip it and come back.
* Don't forget to check the `man` pages of any of the possible helpful commands!
* Google is your friend, don't be afraid to search for answers.

---

### Grade

* Submit all answers to the *CTF Networking Challenge* Pilot quiz.  
* Please work among your table, again: ***communicate***, you can clobber each other's work
* Unlimited retakes so write down your answers
  * I strongly  encourage all students to attempt to run each command themselves!
* Due midnight tonight!

