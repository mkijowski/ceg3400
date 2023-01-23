# Hashcat

* [https://hashcat.net/hashcat/](https://hashcat.net/hashcat/)
* `./data/shadow` file of password hashes
* `./dictionaries/` various wordlists for hashing

---

## The setup

A previous class created user account with dummy passwords and submitted them to me.  Due to a recent bought of Covid, I brain fogged a permission and all of these "secure" password hashes were leaked online.

One of the cse-devteam members found this list floating around and appears to be in a particular format.  The devteam uploaded the file to this repository: 
`./data/shadow`.  Entries look like this:

```
$6$d1gWjURFVstVjUpd$6eBD1QlS7HMwmimKpVeFWUCB9iE7LHaNNlMis3kZLBZhH8vbuUxPaKLFxGYdKnJAWB9i8rEA8vhZiKBhOJEOH0
$6$PD9hEdJXwkI2toeV$YLjTZbAm5PEVMhxuSj3NPPJnUrQ.sh15QpbGsW1PXtJtgCd7yCvnqK/nFj830Vrx9QPahVZUawh397tJuXww60
...
```

Where each line is a section from a user's `/etc/shadow` entry.

In this exercise you will be attempting to recover as many passwords as you can from the supplied shadow file.

You will need to download the dictionaries and shadow file via github website (windows) or via wget as follows:

```bash
wget https://raw.githubusercontent.com/mkijowski/passwords/master/dictionaries/500_passwords.txt
wget https://raw.githubusercontent.com/mkijowski/passwords/master/data/shadow

(dont try this last one in class, it's a doozy)
wget https://github.com/mkijowski/passwords/raw/master/dictionaries/rockyou.txt.gz
```

---

## The attack

***You will need to edit the paths before this will run!!!***

`hashcat -m 1800 -a 0 </path/to/shadowfile> </path/to/dictionaries/500_passwords.txt>`

The above command can be broken down as follows:

* `hashcat` is the program you are running (which might need to be installed)
* `-m 1800` is the hash specification.  `-m` is hashtype and `1800` is for SHA-512(unix) (`man hashcat` -> `/Hash types`)
* `-a 0` is for attack type 0, for straight (`man hashcat` -> `/Attack mode`)
* `<shadowfile> <dictionaryfile>` are the last two arguments hashcat takes and are simply paths to the shadow and dictionary file

Some optional commands that I like to add (after `-a 0`)

* `-o` specifies an output file for us to search later.  By default you can search `~/.hashcat/hashcat.potfile`
* `--remove` removes hash entries from the shadow file after they are found

***A NOT SO OPTIONAL OPTION***

* you will probably need to use `hashcat --force` then the rest of the above options

## Debugging tips:

* Intel CPU's might need the following program installed if hashcat does not run: `sudo apt install intel-opencl-icd`

