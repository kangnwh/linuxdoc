There is an important concept that **all 'things' in Linux are considered as files** - processes, physic memories, physic storage disks, pipelines, sockets are treaded as files. So accessing files is an important way to monitor and control your system.

Comments for the table below :
* `[options]` means the options in it are optional.
* You can use `man command` to see the whole help document in your own computer.
* `$parameter` means the parameter is mandatory.

#### File Accessing
Commands                    |Functionality|Examples
--------|-------|-----
`ls [-trlRad] [path]`|list all files under <path> or current directory if <path> is not provided| <ul><li>`ls -l` --> List all files in current directory in *List Format* </li><li>`ls -a ~` --> List all files under *`~(Home dir)`* include hidden files(whose filenames start with '.')</li><li>`ls -R ~` --> List all files under folder *`~`* recursive, which means it will also show the files in the subfolders of *~* </li></ul>
`cd [path]`| Change directory to the path you provided|<ul><li>`cd ~` --> change the directory to your Home dic</li><li>`cd ..` --> change directory to the parent folder of current folder </li><li>` cd - ` --> change back to the last directory you just changed from </ul>
`pwd`| Show current directory provided|<ul><li>`pwd`</li></ul>
`mkdir [-p] [path]/$folder_name`| Create a folder |<ul><li>`mkdir new_folder` --> Create a folder named *new_folder* under current directory</li><li>`mkdir ~/new_folder` --> Create a folder named *new_folder* under your home directory</li><li>`mkdir -p /new_folder01/new_folder02/new_folder03` --> This will create parents(*/new_folder01/new_folder02*) folders if they are not existing </li></ul>
`more $file_name`| Show the content of the file you provided **page by page** |<ul><li>`more /etc/passwd` --> show the content of file */etc/passwd* . You can hit space button to move down or `u` button to move up. </li></ul>
`less $file_name`| Show the content of the file you provided **page by page** |<ul><li>`less /etc/passwd` --> Same as `more` </li></ul>
`cat $file_name`| Show the content of the file you provided all at once |<ul><li>`cat /etc/passwd` --> The result of this command is almost the same as `more`, but `cat` prints all content at once. </li></ul>
`head [-1 or 2 or 3....] $file_name`| Only show the first n(1 or 2 or 3...) rows of the file you provided.|<ul><li>`head -10 /etc/passwd` --> Show the first 10 rows of file */etc/passwd* </li></ul>
`tail [-f][-1 or 2 or 3...] $file_name`| Only show the last n(1 or 2 or 3...) rows of the file.|<ul><li>`tail -5 /etc/passwd` --> Show the last 10 rows of file */etc/passwd* </li><li>`tail -f ~/.bash_profile` --> Show the last 10 rows for `~/.bash_profile` and waiting, if the file is adding some other content at the same time through other sestion, this command will continue to print them out. This is very useful to monitor the log files of some running application.  </li></ul>
`cp [-r] $source_file $target_file`| Copy a file to another path or name|<ul><li>`cp ~/.bash_profile ~/new_file` --> Copy file `~/.bash_profile` to `~/new_file` </li><li>`cp -r /some/folder ~/` --> `-r` is used to copy folders</li></ul>
`mv $sourc_file $target_file` |Move and rename a file/folder to another path|<ul><li>`touch ~/test_mv` <br/> `mv ~/test_mv ~/rename_mv`<br/> --> These commands will create a file named `test_mv` under your Home directory and rename it to `rename_mv` </li></ul>
`rm [-rf] $file_name or $folder`  | Delete files or folders from the server|<ul><li>`touch ~/test_rm` <br/> `ls -l ~/test_tm` <br/> `rm ~/test_rm` <br/> This will Create a file named `test_rm` under your Home directory and remvoe it. </li></ul>
`vi/vim $file_name` | Edit a text file|<ul><li>`vim ~/.bash_profile` --> Open(or new) file `~/.bash_profile` and you can edit it. The operations for vi/vim are powerful but not very easy for beginners. In most of the cases, you only need to some few commands of [vi/vim](../advanced/vim.md). </li></ul>
`grep -[ei...] $pattern $filename`| |

#### Resource checking
All resources can be monitored via commands in Linux.

Commands |Functionality |Examples
-----------------|----|----
`du -sh $folder or $file`| Show the size of the folder or file with a proper unit.| `du -sh ~` --> Show the size of your home directory
`top` | Full screen application to show the usage of memory/cpu etc. | `top`
`df [-ah] [directory]` | Show the space usage of specific the directory mounts on(remember that all things in linux ar files?). | `df -ah` --> Show all mount points in this system and the usage of their space. We will talk about **mount** later.
`ps [-ef]`| Show the processes running in the server  | `ps -ef|grep usr` --> This command will output all process on the system using standard syntax and then use pipline `|` to pass the result to `grep usr` which will only output the lines containing key word "**usr**"
`netstat -a`|Show all ports that are in use now.| `netstat -a|grep 80` --> This command will first query all ports that are in use and then use `grep 80` to select lines that contains key word "**80**"

#### Advanced Text editing
There are several powerful text editing tools that you can use in your script, but they need some more knowledge about `regular expression` , `streaming programming` and `redirect`.

We will talk about it in the [future](../advanced/advanced-text-editing.md).
