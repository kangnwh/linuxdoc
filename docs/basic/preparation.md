**If you use `Windows system`, please choose one of  3 ways below:**  

**If you use `MacOS`, I also recommend you to set up an virtual environment for your learning because it can protect your computer from being crashed:**

0. Use another remote server.

1. Refer to *[Virtual Machine](../virtual-machine-setting.md)* to set up a virtual Linux environment.(Recommanded)

2. Using a online Linux emulator system, such as *[this](https://www.tutorialspoint.com/unix_terminal_online.php)* (Not recommanded)




Let's begin from the most common ones:  

### Preparation   

You need a software which can connect with your Linux server via SSH protocol so that you can * ** control ** * your Linux just using commands.
> SSH like Windows Remote Controller - You can use SSH & Shell commands to control your server.

* If you use Windows systems, you may need *[PuTTY](http://www.putty.org)* or something you like to connect to the server
* If you use MacOS, just open your `Terminal` (if you do not know how to open it, you may be not prepared for this document...)
* If you \*unix systems, you may not need to go through this document...

** something like this: **
![Screenshot](../img/terminal.png)

There are 3 areas marked in the picture. All this information can be changed if you update the environment variable `PS1`, which we will discuss it in the next section.


### Environment Variables
Lots of configurations of Linux are controlled by `environment variables`. A simple example is the one we mentioned above - the shell prompt:

```Shell
    eric@LabServer:~ %  
      # eric : the current login user
      # LabzServer : the server hostname
      # ~ : the working directory (~ means the home directory of the current user)
```
This appearance is controlled by an environment variable - `PS1`.
OK, let's make it something cool:

```Shell
export PS1="------ This is my computer ! Don't touch ! ----- "
```
** Now we get: **
![Screenshot](../img/PS1.png)

What if we want something dynamic? Such as we want to see the date and the sequence number of our command in this section?

** Example **
```Shell  
export PS1="Today:\d ||User: \u || Command# :\# "  
    # \d -> Show current date
    # \u -> Show current user
    # \# -> Show the sequence number of commands in this section

```
![Screenshot](../img/ps1-date-number.png)

**Let me explain what happens:**  
1. `export` -> this key word indicates that the variable   assignment operation also works in its parent process(it is a little complex, we will talk about it in Script section)  
2. `PS1="Today:\d ||User: \u || Command# :\# "` -> This is an assignment:
>
  * "Today:..||User:...|| Command#" :-->These words are normal words, just as what they are showing  
  * \d --> A placeholder that tells Linux to put current date here.  
  * \u --> A placeholder that tells Linux to put current username here.  
  * \# --> A placeholder that tells Linux to put the command sequence number of this section.  


You can reference *[here](https://www.cyberciti.biz/tips/howto-linux-unix-bash-shell-setup-prompt.html)* for more information about the placeholders in `PS1` variable.

** Lots of other variables can be found **
Use command showing below to have a big picture about what kinds of environment variables you may have:
```shell
printenv
```
This command will print all variables at once but you may have some problems on scrolling up/down. Try this:
```shell
printenv|more
```
* `|` symbol is a `pipline`, which can pass the output of previous one to the next one.In this case, the output of `printenv` will be passed to `more`
* `more` is command to print content of files ** pages by pages ** . So that you will see the picture showing below and you can just hit blank for next page:
![Screenshot](../img/printenv_more.png)
