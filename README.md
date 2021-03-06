# simpl
simpl is a "Security IMplied Password Locker"

As stated, simpl is a password locker. The idea behind it is a small, lightweight, but secure, password locker.

simpl has not been audited; therefore, you are admonished to use at your own risk. It has been developed with the best cryptographic libraries available for Python and any security issues brought to my attention will be taken care of ASAP.

In regards to not being audited, I welcome anyone to audit it, if they wish. Until a proper audit has been performed, it is in your best interest to not rely on the security of this software and treat it as potentially insecure. 

I have developed simpl to learn more about cryptography and its practical applications.

If you want to contribute, please keep in mind that your additions must stay within the realm of "Simple and Lightweight".

simpl is released under the GPLv3! Please share it, fork it, whatever! 

# Detailed Command List

Simpl is made to be easy and quick. There is no GUI, it's all run in the command-line and the commands are really simple, and, for some, familiar.

* `help|?` - Displays a non detailed list of commands.
* `exit|:q|:wq` - Exits the program. No need to save, that's done immediately after you make any changes to your entries.
* `add|touch|new|create [account name] [username]` -  Adds a new entry to your Locker. 
* `cat|type [account name]` - Pulls all information specifically for the account you provide to avoid displaying unneeded information.
* `list|ls|dir` - Lists all accounts in Locker. Shows only account name and the comment, if available.
* `delete|del|remove|rm [account name]` - Deletes entry from locker by account name.
* `update|modify|mod|change <account name> <username>[=value, <comment>=<value>, <password>]` - Updates the entry using a very specific syntax. It requires an account name AND at least one attribute. You can specify the update by using an `=` followed by the value you want to set it to. You can specify multiple attributes by seperating them with a comma. This can be done in any order. NOTICE: Although, you can use this to update the password, it is not reccommended because it can be seen in plaintext. Instead, specify that you want to update the password by specifying the plain attribute `password`, and it will prompt you in a secure, non-echoing manner.
* `<query>` - Anything that does not fit the above commands will act as a search on all the entries. If it finds the term you enter in an entry, it will display all the info from that entry.

# FAQ

* Q: Where is the Locker file stored? A: It's stored in your home directory as `.simpl`. Do not modify or change anything in the file. If you do, it will get corrupted and, if you cannot revert it, you will lose your information. This file is encrypted, so if you used a strong key, there is, theoretically, little to no chance that someone can recover this information. This makes it safe to backup elsewhere. 
* Q: Has Simpl been audited? A: No, it has not. However, I welcome anyone to audit it. Simpl uses the PyCrypto library which is pretty trustworthy, though.
* Q: Does this work on Windows? A: I don't know. I haven't tested it on Windows, and, frankly, I don't want to. You're welcome to test it yourself and submit a pull request if neccessary.
* Q: I forgot my password, is there a way to recover it? A: Nope, sorry. Implementing password recovery will undermine the strength and integrity of Simpl.
* Q: What encryption does Simpl use? A: It uses AES-256 in CBC (Cipher Block Chaining) mode. It's only as secure as your key, so make your key at least 50 bits of entropy, however, I personally use at least 70 bits.
* Q: I can't see the password when I `cat` the entry, why not? A: Simpl uses the termcolor library to color the text so that no one can shouldersurf the password from you. To get it, you must highlight the password. It's up to you to clear your clipboard.

# Security Limitations
If you read the [Cryptography Library's documentation](https://cryptography.io/en/latest/), you will see the following warning:

> [Memory wiping](https://blogs.msdn.microsoft.com/oldnewthing/20130529-00/?p=4223/) is used to protect secret data or key material from attackers with access to uninitialized memory. This can be either because the attacker has some kind of local user access or because of how other software uses uninitialized memory.

> Python exposes no API for us to implement this reliably and as such almost all software in Python is potentially vulnerable to this attack. The [CERT secure coding guidelines](https://www.securecoding.cert.org/confluence/display/c/MEM03-C.+Clear+sensitive+information+stored+in+reusable+resources) assesses this issue as “Severity: medium, Likelihood: unlikely, Remediation Cost: expensive to repair” and we do not consider this a high risk for most users.

I have included the above warning to showcase Python's shortcomings when it comes to cryptographic applications. Again, as stated above, use at your own risk.
