### SPASS Password Creator

---

The **SPASS** password creator is a simple and customizable BASH script.  
As long as the input is always the same the output will always be the same.   
It will produce secure passwords from simple input words or phrases. With **SPASS** there is no need to remember complex inputs.  
Below I will break down the script so that you know how to personalise it for yourself.

---

##### Type Something In

`read -p "Your Input:  " ; echo $REPLY`

The first part of the script simply waits for you to type something in.  

`| sha256sum`

Your input is piped to SHA256 and produces a hash value.
The output of the **sha256sum** is 64 characters long. It's important to know this for the next stage.  

`| cut -b 5-16`

The *cut* commands are the most important. This is where you determine which portion of the 64 character output is that you are going to use for the next operation. This range will be personal to you.

`| sha256sum`

The range that you selected is then piped into SHA256 to be hashed again.  

`cut -b 20-43 && echo "Here is your password."`

The last part of the script uses the *cut* command again not only to determine where the starting point of your password is within the hashed output but also how long that password should be.  
A message then tells you that the process is complete alongside your password. This can also be personalised.  

---

##### The Script

`read -p "Your Input:  " ; echo $REPLY | sha256sum | cut -b 5-16 | sha256sum | cut -b 20-43 && echo "Here is your password."`

##### Enjoy

I hope you find this script useful.  
I have been using it for a while.  
The **sha256sum** command doesn't output any special characters and so I'd give it a medium security rating.  

If you want to change, add to or generally improve this script please feel free to do so.