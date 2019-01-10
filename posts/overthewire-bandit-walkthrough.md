.. title: OverTheWire: Bandit - Walkthrough
.. slug: overthewire-bandit-walkthrough
.. date: 2019-01-10 12:05:12 UTC-05:00
.. tags: ctf, hacking, walkthrough, overthewire
.. type: text

** NOTE: Levels 24-35 have been added to Bandit, and I will be including them in a 
separate walkthrough **


## Using this guide:
If you are copy/pasting these solutions, YOU ARE WRONG! That is NOT what this walkthrough is for. If you read the documentation, excercised your google-fu, experimented and still don't know how to proceed.. then you refer to the number and solution below. See what the correct answer is, figure out WHY it is the correct answer, and only then type it in yourself and continue. Anything short of this is doing you no favors.

### OverTheWire
Overthewire.org hosts a litany of machines available for those who desire to learn or practice 
their infosec skills. Their boxes start at 'no skill' and increase in difficulty. OTW provides 
this service for free to the public, so I strongly encourange anyone who 
uses or benefits from it to drop them a donation to help keep them up! 

### Bandit
The bandit machine is an introductory box used to teach the basics of Linux and server 
administration. It is accessed and completed through SSH. To start the 
challenges, all you need to do is drop ```ssh bandit0@bandit.labs.overthewire.org -p 2220``` 
into your 
terminal. If you are having trouble or struggling or can't figure out how you are supposed to 
progress to the nexel stage <a 
href="https://overthewire.org/wargames/bandit/">overthewire</a> has a level by level set of 
instructions.

### The Walkthrough:
The majority of the 'levels' on bandit can be completed in under 1 minute. Yes, this box is 
that easy. As such, I'm only going to provide you with the minimum amount of information needed 
to complete each level. If you don't understand how the tool or command works I STRONGLY 
encourage you to read the informative links provided for each level on <a 
href="https://overthewire.org/wargames/bandit">overthewire</a>.

<pre>
bandit0: cat readme
bandit1: nano + CTRL+R +'-'
bandit2: cat spaces\ in\ this\ filename
bandit3: ls -la inhere
bandit4: find inhere ! -executable -readable
bandit5: find inhere -readable ! -executable -size 1033c
bandit6: find / -user bandit7 -group bandit6 -size 33c
bandit7: cat data.txt | grep millionth
bandit8: cat data.txt | sort | uniq -u
bandit9: strings data.txt | grep ==
bandit10: base64 -d data.txt
bandit11: cat data.txt | tr a-zA-Z n-za-mN-ZA-M (OR rot13.com)
bandit12: -- 
	cat data.txt | sort | uniq -u
	file data.txt
	zcat data.txt > datanew
	file datanew
	bzip2 -d datanew
	file datanew.out
	zcat datanew.out > datanew
	file datanew
	tar -xvf datanew
	file data5.bin
	tar -xvf data5.bin
	file data6.bin
	bzip2 -d data6.bin
	file data6.bin.out
	tar -xvf data6.bin.out
	file data8.bin
	zcat data8.bin > holycrap
	file holycrap
	cat holycrap
bandit13: ssh -i sshkey.private bandit14@localhost  (This is an internal pivot!!)
bandit14: telnet localhost 30000 
		* submit password of current level to the server
bandit15: openssl s_client -connect localhost:30001 
		* submit current level pass again
bandit16: --
	nmap -sV -p 31000-32000 localhost
	openssl s_client -connect localhost:31790
	(submit current level pass)
	mkdir /tmp/obfuscated-name
	cd /tmp/obfuscated-name
	 * copy RSA key from SSL connection
	vi sshkey.private
	 * save it
	chmod 600 sshkey.private
	ssh -i sshkey.private bandit12@localhost	  
bandit17: diff passwords.new passwords.old
bandit18: ssh bandit18@bandit.labs.overthewire.org cat readme
bandit19: ./bandit20-do cat /etc/bandit_pass/bandit20
bandit20: --
	nc -l 7331
	  * CTRL+Z
	./suconnect 7331
	  * CTRL+Z
	jobs 1
	  * submit current password
	  * CTRL+Z
	jobs 2
	  * suconnect pushes password
	  * CTRL+Z
	jobs 1
	(please make sure all processes are stopped before you exit!!)
bandit21: --
	cat /usr/bin/cronjob_bandit22.sh
	cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
bandit22: --
	cat /etc/cron.d/cronjob_bandit23
	cat /usr/bin/cronjob_bandit23.sh
	sh /usr/bin/cronjob_bandit23.sh
	echo I am user bandit23 | md5sum | cut -d ' ' -f 1
bandit23: --
	cat /etc/cron.d/cronjob_24.sh
	mkdir /tmp/skjdhf
	cd /tmp/skjdhf
	echo "cat /etc/bandit_pass/bandit24 >> /tmp/skjdhf/pass.txt" > myscript.sh
	chmod 777 myscript.sh
	chmod -R 777 /tmp/skjdhf
	cp myscript.sh /var/spool/bandit24
		* wait ~1min
	cat pass.txt


</pre>
