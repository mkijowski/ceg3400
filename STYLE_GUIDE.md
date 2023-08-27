## Guide to markdown style

[Follow this markdown cheat-sheet](https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet)

* When in doubt ask or use your best judgment
* Move answers to a new line as much as possible.
* Use back-tics (\`example\`) to highlight commands, arguments, and files/paths.
* Use triple back-tics to highlight whole sections of code, multiple lines of output, or portions of a file.
* [Write good commit messages](https://chris.beams.io/posts/git-commit/), but I wont grade them...
* Make it look good!
* pro tip, make it look good both in text format and markdown format

---

## Keeping answers inline

When answering questions, keep them in-line but below the question.  Below are ***good*** responses.

####

* What is in your markdown file:
  
```markdown
* For instance, what is your favorite color

  Blue

* Next question
  * next answer
```


#### How it renders on Github:
  
* For instance, what is your favorite color

  Blue

* Next question
  * next answer


Notice the extra newline between the first question and answer, this is required to have it shown in a new paragraph. 
The indentation before the answer allows it to be a part of the same bullet point 

---

### Bad examples

#### Markdown file contents

```markdown
* What is your favorite food
  pizza
```

#### Github render

* What is your favorite food
  pizza

---

#### Worse yet, Markdown file contents:

```markdown
* What is your favorite color?
* What is the hex value of that color?
* How many of that color items are in your backpack?
Blue
000ff
13
```

#### Github render:

* What is your favorite color?
* What is the hex value of that color?
* How many of that color items are in your backpack?
Blue
000ff
13

---

## Code highlighting

Files (especially paths) and commands can be surrounded by single back-tics  \`example\` -> `example`

Triple back-tic allow for multi line code highlighting, useful for pasting the output of commands (may need to view raw for this):
```
mkijowski@pop-os:~/3400$ ls -lah
total 232K
drwxrwxr-x  4 mkijowski mkijowski 4.0K Sep 20 22:05 .
drwxr-xr-x 26 mkijowski mkijowski 4.0K Sep 20 23:27 ..
-rw-rw-r--  1 mkijowski students  198K Sep 20 09:12 allkeys
-rwxrwxr-x  1 mkijowski mkijowski  112 Sep 19 10:19 coingrader.sh
drwxrwxr-x  2 mkijowski mkijowski 4.0K Sep 20 17:18 dictionaries
-rw-rw----  1 mkijowski grader    1.4K Sep 14 20:05 key-sign-grades
drwxrwxr-x  2 mkijowski mkijowski 4.0K Sep 20 18:02 lab1
-rwxrwxr-x  1 mkijowski mkijowski  413 Sep 14 14:15 miner.sh
-rw-------  1 mkijowski mkijowski   16 Sep 20 22:05 private-key
```

Note: triple back-tics will not line wrap, so you should probably format that a little bit yourself...

---

Be careful when using code blocks, they should ***ONLY*** be used for code, and the code should be well spaced or else you get something that looks like this and is mostly unreadable, especially if the answer you are looking for is 42.

```
Be careful when using code blocks, they should ***ONLY*** be used for code, and the code should be well spaced or else you get something that looks like this and is mostly unreadable, especially if the answer you are looking for is 42.
```
