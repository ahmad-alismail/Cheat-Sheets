* Google: How to <your_question> from **terminal**?
* Check out this [comprehensive command line reference](https://ss64.com/) for more details

Command | Description
------------ | ------------
``<command> --help`` | get help about any command
``cd`` | Change Directory
``cd ..`` | move up one directory
``cd \`` | move up to root
``mkdir`` | make directory
``ls`` | list files and dir
``mv <source> <destination>`` | **move** folder dir if the destination exists, if not **rename** the source with name of the destination
``mv <source> ..\`` | move file/folder to the root dir
``cp -r <source> <destination>`` | **copy** the source folder **recursively** (with subdirectories) into destination if exists, if not, destination will be **created**
``rm -r <dir>`` | remove directories and their contents **recursively**
``echo "my_text_here" > ahmad.txt`` | print text or string data into the terminal or another command as input or a file if the file exists (**> overrides text in original**), if not, it will be created.
``echo "additional_text_here" >> ahmad.txt`` | print text or string data into the terminal or another command as input or a file if the file exists (**>> appends text in original**), if not, it will be created.
``cat ahmad.txt osama.txt or *`` | display the content of a file in text format. It can be used to view multiple files, create a blank file, redirect a file content to other tools, etc.
``cat original.txt orig2.txt > new.txt``| copy the text in original.txt and orig2.txt into new file called new.txt and **overrides** it if new.txt exists
``cat original.txt orig2.txt >> new.txt``| copy the text in original.txt and orig2.txt into new file called new.txt and **appends** it if new.txt exists
``grep "keyword_search" filename1 filename2``| searches for a particular expression pattern in a specified file. When it finds a match, it prints all the lines of a file that matched the specified pattern. It comes in handy when you have to filter through large log files.
``grep "keyword_search" -r <dir>``| search for string in a directory **recursively**, prints all the lines of a file that matched the specified pattern. 
``grep "keyword_search" -r -l <dir>``| search for a file name in a directory  (**recursively**) that contains a specific string in it 
``file *``| show all files types
``file xyz.ab``| show the file's type 
``touch abc.xyq``| create a file 
``any command /?``| show the usage of a command 
``Ctrl + c``| stop any running process 
``tree /a``| see all folders and files as a tree 
``osk``| use a keyboard on your screen 
``tasklist``| use the task manager
``alias``| showing shortcuts list 
``alias os=ahmad_command``| create shortcut for ahmad_command
``ahmad_command1 && ahmad_command2``| run two commands at the same time 
``whoami``| showing user name 
``systeminfo``| showing all system informations 
``ahmad_command > filename.txt``| pushing result of command in filename 
``ipconfig``| showing network's information 
<code> ahmad_command &#124; clip </code> |  copy command's result into clipboard

