---
title: "These are my writeups"
---
# What is this

Hi! I'm a student from belgium and I am working on my pen testing. With this blog I wanted to share my road and experience in becoming a good pentester. Right now I am trying to solve as much boxes on TryHackMe.com. 

* ![Pickle Rick Writeup](https://jorik-vanlooy.github.io/THM-blog/#PickleRick)


## PickleRick
My first real box to attack is the pickle rick box. First thing to do is to run an nmap scan on the box.
![nmap scan](https://github.com/Jorik-VanLooy/THM-blog/blob/THM_writeups/pickle-rick/nmap-scan-Pickle-rick.png)

The result as we can see is that it is an ubuntu box running a webserver on port 80. Let's see what this is all about.

Apparently rick has turned himself into a pickle and he has a reverse formula. He has the ingredients on his pc but he forgot his credentials. Let's get to it.

![home page](https://github.com/Jorik-VanLooy/THM-blog/blob/THM_writeups/pickle-rick/home-page.png)

first things first, we are still in recconaissance mode. Let's see if the webpage has hidden directory's or files. I'm going to be using gobuster for this.

![gobuster1](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/gobuster.png)

We have a hit on a robots.txt file. This file basicaly is a hidden files that tells search engines to not show certain files/directory's in the results of search engines.

![robots.txt](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/Robots-pickle-rick.png)

There is one of the many catchphrases of rick. This could be usefull for later!

![source](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/source-pickle-rick.png)

Another thing we can do to find information is to look in the source code, sometimes developers leave comments in there. We found a username, this means there needs to be login page somewhere and a password.

![gobuster2](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/gobuster-part2-pickle-rick.png)

So I start a second gobuster to find hidden files, this time with php. A popular coding language to make dynamic web pages with a db in the backend. It worked and we found a login.php page, let's try it!

![login](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/login-pickle-rick.png)

The username and the chatchphrase worked! we come to a input field were we can try out some commands.

![command screen](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/portal-pickle-rick.png)

![first command](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/ls-pickle-rick.png)

Let's check out what we can find in the directory. There is a intereting file and a clue lets's open them.

![command disable](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/command-disable-pickle-rick.png)

Oh no! This doesn't work. The command is disabled. Well if we go back we can see that the file is in the root directory. Maybe we can read it when we go to it in the url of the webbrowser..

![succes](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/first-ingredient.png)
![succes](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/clue-pickle-rick.png)

Now we can get on an adventure in the system, first thing to do is to look for the users, they are located in hte /home directory.

![location second](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/found-location-pickle-rick.png)

Succes in the rick directory is another ingredient!! But how do we open it? cat is blocked but there are other command to open files with. Let's try them.

![less is more](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/less-ingredient-pickle-rick.png)

It didn't take long, second command i tried was more, didn't work. Third command was less, that was a success, we found it. Now we need to find the third one, we need sudo rights for this one simple way to check them is sudo -l

![sudo -l](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/sudo-l-pickle-rick.png) 

We notice that we have the right to execute every command with sudo rights.

![sudo root](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/sudo-root-pickle-rick.png)

we can see the 3rd ingredient in the root directory let's use sudo less and get the third one!!.

![sudo less](https://github.com/Jorik-VanLooy/THM-blog/blob/THM-writeups/pickle-rick/3rd-ingredient-pickle-rick.png)

We have the third and final ingredient. Soooo we are done here. I think that this is a nice box to play, I have solved it in one way but there are many ways to solve this one. I hope my writeup is good and clear.

See you on the next one!
