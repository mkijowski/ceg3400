## In Class Exercise: Wildcard Injection

[AWS environment link (could be a CSRF)...](https://console.aws.amazon.com/cloudformation/home?region=us-east-1#/stacks/new?stackName=ceg3400WILDCARD&templateURL=https:%2F%2Fwsu-cecs-cf-templates.s3.us-east-2.amazonaws.com%2Fcourse-templates%2Fceg3400-wildcard.yml)

* IP address: get from AWS
* username: `sudoless`
* SSH key: `sudoless.pem` in this git folder

---

You have "acquired" access to a linux system as a non priveleged user
named `sudoless`.  After loitering around on the system you find out that
the administrator has set up a trivial home directory backup script that runs
every minute.  The script looks like this:

```bash
#!/bin/bash
cd /home/sudoless
tar -cpf /home/ubuntu/backup.tar.gz *
```

Remembering something that Kijowski once complained about in class, you
realize that this script is likely vulnerable to a command injection.

Your mission is to turn the `sudoless` user into a sudo user by injecting some malicious information into one of the executions of the above backup script.

Some hints:

* Think back on the the `rm *` example in class
* A simple way to gain sudo for a user is to add a line to the `/etc/sudoers` file
* You will need to write an executable script in your home directory that does the heavy lifting (something bad)
* You will need a way to pause the tar file creation, maybe with a `--checkpoint=1`  (check the `man tar` page)

