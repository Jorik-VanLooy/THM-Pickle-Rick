---
title: "Pickle Rick write up"
---
# What is this
This is a write up of the pickle rick box on Try Hack Me. I had fun exploiting this box, This box covers basic web pentesting.


## PickleRick
My first real box to attack is the pickle rick box. First thing to do is to run an nmap scan on the box.
![nmap scan](/pickle-rick/nmap-scan-Pickle-rick.png)

The result as we can see is that it is an ubuntu box running a webserver on port 80. Let's see what this is all about.

Apparently rick has turned himself into a pickle and he has a reverse formula. He has the ingredients on his pc but he forgot his credentials. Let's get to it.

![home page](/pickle-rick/home-page.png)

first things first, we are still in recconaissance mode. Let's see if the webpage has hidden directory's or files. I'm going to be using gobuster for this.

![gobuster1](/pickle-rick/gobuster.png)

We have a hit on a robots.txt file. This file basicaly is a hidden files that tells search engines to not show certain files/directory's in the results of search engines.

![robots.txt](/pickle-rick/Robots-pickle-rick.png)

There is one of the many catchphrases of rick. This could be usefull for later!

![source](/pickle-rick/source-pickle-rick.png)

Another thing we can do to find information is to look in the source code, sometimes developers leave comments in there. We found a username, this means there needs to be login page somewhere and a password.

![gobuster2](/pickle-rick/gobuster-part2-pickle-rick.png)

So I start a second gobuster to find hidden files, this time with php. A popular coding language to make dynamic web pages with a db in the backend. It worked and we found a login.php page, let's try it!

![login](/pickle-rick/login-pickle-rick.png)

The username and the chatchphrase worked! we come to a input field were we can try out some commands.

![command screen](/pickle-rick/portal-pickle-rick.png)

![first command](/pickle-rick/ls-pickle-rick.png)

Let's check out what we can find in the directory. There is a intereting file and a clue lets's open them.

![command disable](/pickle-rick/command-disable-pickle-rick.png)

Oh no! This doesn't work. The command is disabled. Well if we go back we can see that the file is in the root directory. Maybe we can read it when we go to it in the url of the webbrowser..

![succes](/pickle-rick/first-ingredient.png)
![succes](/pickle-rick/clue-pickle-rick.png)

Now we can get on an adventure in the system, first thing to do is to look for the users, they are located in hte /home directory.

![location second](/pickle-rick/found-location-pickle-rick.png)

Succes in the rick directory is another ingredient!! But how do we open it? cat is blocked but there are other command to open files with. Let's try them.

![less is more](/pickle-rick/less-ingredient-pickle-rick.png)

It didn't take long, second command i tried was more, didn't work. Third command was less, that was a success, we found it. Now we need to find the third one, we need sudo rights for this one simple way to check them is sudo -l

![sudo -l](/pickle-rick/sudo-l-pickle-rick.png) 

We notice that we have the right to execute every command with sudo rights.

![sudo root](/pickle-rick/sudo-root-pickle-rick.png)

we can see the 3rd ingredient in the root directory let's use sudo less and get the third one!!.

![sudo less](/pickle-rick/3rd-ingredient-pickle-rick.png)

We have the third and final ingredient. Soooo we are done here. I think that this is a nice box to play, I have solved it in one way but there are many ways to solve this one. I hope my writeup is good and clear.

See you on the next one!
