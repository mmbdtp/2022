---
title: Monday Morning — Introducing Unix
---

# Monday Morning — Introducing Unix

Credits for today's sessions: material reworked from previous workshops by Andrea Telatin and fresh material from Mark Pallen. ChatGPT used to proofread, expand on points and create images.

|||
| Learning Objectives | |
|| Demonstrate the usefulness of the command line |
|| Learn basic commands for navigation and file manipulation |
|| Signpost useful resources and topics for learning shell |
|||


## Be excited! Be very excited! 

![](https://raw.githubusercontent.com/mmbdtp/mmbdtp.github.io/gh-pages/modules/UNIX/_posts/excited.jpg)

Welcome to this introductory tutorial on using the Unix command line on your MacBooks. The command line is a powerful tool, enabling users to perform tasks more efficiently and automate processes. In this tutorial, we will explore the basics of navigating the file structure, creating and deleting files and directories and some essential Unix commands.

As we go along feel free to interrupt and ask questions, if anything is unclear or not working for you. Demonstrators will be walking around the room checking that all is well. 

If you want to raise questions or share insights, please add text or links to this Google Doc:

* [https://tinyurl.com/MMBDTP-doc](https://tinyurl.com/MMBDTP-doc)

Most of the week will be taken up with hands-on sessions, but before you get your hands dirty, let's start with a brief [PowerPoint presentation](https://github.com/mmbdtp/mmbdtp.github.io/raw/gh-pages/githubio/2023_course/week_1/2023_Week1_Command_line_Unix.pptx) to set the scene.


---

### Why do we need to use the command line?

|||
|More tools and functionality||Developing graphical user interfaces is costly and time consuming. Many bioinformatics tools do not have a GUI and those that do often have more functionality when using the command line.|
|||
|Scalability, reproducibility and reliability||Sharing a line of code is quicker and less error prone than describing a sequence of mouse clicks. A command can be rapidly ran multiple times and can be inspected for mistakes.|
|||
|Accessing larger computing resources||More intensive bioinformatics tasks require more computing resources, many of which can only be accessed via the command line.|
|||

---


### Opening the Terminal App

Okay, let's get started! 

Click on the magnifying glass icon (`Spotlight`) in the top-right corner of your MacBook screen.

Type `Terminal` and press `Enter`. then double-click on `Terminal.app`

Alternatively, you can open the `Applications` folder, then `Utilities` and double-click on `Terminal`.

- After you have opened the `Terminal` , if you mouse over the icon for the `Terminal`  in the Dock and select _Options_, you can tell macOS to keep the icon available in your Dock.

You should now see a window with a **command-line prompt**.


```
username@computername ~ %

```
The command-line prompt typically displays the name of your computer, the current working directory and your username. It ends with a `%` sign, waiting for you to enter a command. 

The command line prompt can be customised to say almost anything, this is just the default zsh prompt.

When you first open the Terminal app, you are likely to find yourself in your home directory associated with your username and account on the MacBook.

The terms `Terminal` and `shell` are often used interchangeably, but they refer to different things.

* **Terminal**: This is the actual interface or program that opens a window and lets you interact with the shell. The terminal displays input and output. It's the graphical or text-based application you run, like the Terminal app on macOS or programs like iTerm2.
* **Shell**: The shell is the environment or command-line interpreter that processes commands. When you type commands into a terminal, it's the shell that reads, interprets, and executes those commands. There are various shells available, with `bash` being one of the most common, especially on Linux. You will see lots of online material mentioning the `bash` shell. Others include `sh, zsh, csh`, and `fish`.

When you're using the `Terminal` app on macOS, you're typically using the Z shell or  `zsh` within that terminal to execute commands. If you need to switch to another shell, say `bash`, you type its name. 

Let's switch to `bash`. 


```
bash
```

And then back to `zsh`. 

```
zsh
```

A few links

* [https://en.wikipedia.org/wiki/Unix_shell](https://en.wikipedia.org/wiki/Unix_shell)
* [https://en.wikipedia.org/wiki/Bash_(Unix_shell)](https://en.wikipedia.org/wiki/Bash_(Unix_shell))
* [https://en.wikipedia.org/wiki/Z_shell](https://en.wikipedia.org/wiki/Z_shell)


---


### Navigation: macOS Finder vs Terminal

- **Finder** : You navigate through files and folders by clicking on them.
- **Terminal** : You navigate by typing commands then pressing the Return key

Navigate to your `home directory` and then to the `Desktop` directory using the Finder. Now let's navigate to the `Desktop` on the `Terminal` and create some directories and files there.

```bash
$ cd Desktop

```
In this command `cd` (short for "change directory") changes your current directory to the `Desktop` directory. You type the command, then a space and then the name of the file or directory you want the command to act on. This is how most Unix commands work. 

Almost all Unix commands also have Wikipedia entries.

- [https://en.wikipedia.org/wiki/Cd_(command)](https://en.wikipedia.org/wiki/Cd_(command))
- [https://en.wikipedia.org/wiki/List_of_Unix_commands](https://en.wikipedia.org/wiki/List_of_Unix_commands)


Here's a cheat sheet of UNIX commands from Fosswire: 
- [Unix/Linux Command Cheat Sheet](https://files.fosswire.com/2007/08/fwunixref.pdf)

ChatGPT ([https://chatgpt.com](https://chatgpt.com)) will also give good answers to well posed questions about what a Unix command does and how to get the best out of it. Try asking it to tell you about the command `cd`, the common problems with using `cd` or a joke related to `cd`.


---


### Making directories and files
Let's make a new directory in the `Desktop` folder

```bash
$ mkdir bioinfo_adventures

```
The `mkdir` command is used to create a new directory. You type the command, then a space and then the name of the directory you want to create, which here we are calling `bioinfo_adventures`.

Take a fresh look at the Desktop folder using the Finder and you will see this new empty directory as a folder there.

Let's move inside that new directory using the command line.

```bash
$ cd bioinfo_adventures

```
Let's use the `touch` command to create an empty file
- Note that the touch command in Unix-like operating systems is primarily used for creating empty files or updating the timestamps of existing files.



```bash
$ touch grandeur.txt

```

Look at the file `grandeur.txt` on the Finder. Click on it. You will see it is empty.

Let's add some text.

```bash
Nano grandeur.txt

"There is grandeur in this view of life"

```

Nano is bash based text editor (there are many available) which allows you to make edits to `grandeur.txt`. 


Click on the `grandeur.txt` file in the Finder and you can see it now contains the text.


---


### File extensions
In Unix, file names can have extensions (such as .txt, .jpg, or .sh) to indicate the file type or its intended use, but these extensions are not mandatory for the system to recognize or handle the file. Unlike some operating systems (e.g., Windows), Unix doesn’t rely on file extensions to determine a file's type. Instead, Unix uses a file’s metadata or inspects the file contents through programs like `file` to identify its format. For example, while a text file might have a .txt extension for clarity, Unix would still be able to manipulate the file without an extension based on the actual content or the program interacting with the file.

```bash
$ file grandeur.txt

```


---


### Naming Conventions: Finder vs Terminal 

- **Finder**: allows filenames with spaces. Not case sensitive.
- **Terminal**: Creates difficulties for filenames with spaces; instead we tend to use underscores or quotes. Case-sensitive

Let's see what happens when we make a directory on the command line with a name containing spaces.


```bash
$ mkdir "bioinfo fun"

```
Putting quotes around the name allows us to create a file or directory name that contains spaces

- Warning: these have to be straight quotes! Microsoft often corrects these to curly quotes, so be careful when pasting from Word documents. 

An alternative approach is to escape the space using a backslash `\`

```bash
$ mkdir bioinfo\ fun

```
If you type those two commands one after another, you will get an error message saying `File exists`. 

- Sometimes Unix gives this kind of useful feedback, sometimes it does not! It can be a demanding and inconsistent tool.

If you look via the Finder you will see the directory `bioinfo fun` is sitting there. But what happens when you try to move into it on the command line?

```bash
$ cd bioinfo fun

```
You get told `no such file or directory`!

To avoid this problem, we generally use the underscore character `_` to represent white spaces in Unix file names, which also means we don't need the quote marks.

```bash
$ mkdir bioinfo_fun

```

And now let's move into `bioinfo_fun`

```bash
$ cd bioinfo_fun

```
Note that in Unix both commands and file names are generally case sensitive. 

macOS is forgiving if you type `Cd Bioinfo_fun` or `CD bioinfo_fun` instead of `cd bioinfo_fun` 

But most Unix-like systems will fail to recognise the file name if any character is not in the right case.


---


### Escape characters

It's worth spending a few minutes picking up on that idea of escape characters.

In Unix-like operating systems, certain characters have special meanings in the shell, which can cause issues when used in file names. These characters might be interpreted as commands or part of the command syntax. **Escape characters** allow you to handle these special characters in file names by neutralizing their effects, ensuring they are treated as literal characters.

### Common Special Characters in File Names:
Some characters that need to be escaped or handled carefully include:
- **Spaces** (` `)
- **Dollar sign** (`$`)
- **Asterisk** (`*`)
- **Ampersand** (`&`)
- **Exclamation mark** (`!`)
- **Backslash** (`\`)
- **Parentheses** (`(` and `)`)
- **Brackets** (`[` and `]`)
- **Single quote** (`'`)
- **Double quote** (`"`)
- **Pipe** (`|`)
- **Semicolon** (`;`)
- **Angle brackets** (`<` and `>`)
- **Tilde** (`~`)

If these characters are used in file names without proper handling, the shell may interpret them as commands, arguments, or metacharacters (wildcards), leading to unexpected behavior.


---


### Ways to Escape Characters in File Names:

1. **Backslash (`\`) Escape:**
   - Use a backslash before a special character to escape it, so the shell interprets it as a literal character rather than a special one.
   - Example: Escaping a space in a file name.
     ```bash
     touch file\ name.txt
     ```
     This will create a file called `file name.txt` instead of interpreting the space as a separator.

   - Another example: Escaping an ampersand (`&`).
     ```bash
     mv file\&name.txt newfile.txt
     ```

2. **Single Quotes (`' '`) Around the File Name:**
   - Enclosing the file name in single quotes treats everything inside as a literal string, including special characters.
   - Example: Creating a file name with a space and exclamation mark.
     ```bash
     touch 'file name!.txt'
     ```
     This will create a file named `file name!.txt`.

   - Single quotes are useful when dealing with complex combinations of special characters, as they neutralize everything inside the quotes.

3. **Double Quotes (`" "`) Around the File Name:**
   - Double quotes work similarly to single quotes but allow for variable and command substitution (unlike single quotes, which treat everything literally).
   - Example:
     ```bash
     touch "file name with spaces.txt"
     ```
     This will create a file called `file name with spaces.txt`.

4. **Using `\` or Quotes in File Paths:**
   - You can use backslashes or quotes when dealing with paths that contain special characters.
   - Example:
     ```bash
     cd /home/user/special\ folder/
     ```
     or
     ```bash
     cd "/home/user/special folder/"
     ```


---


### Special Characters and Their Effects:

1. **Spaces (` `):**
   - If not escaped, spaces are interpreted as separating arguments. For instance:
     ```bash
     mv file name.txt
     ```
     This will try to move `file` and `name.txt` separately, which is not the intention. Escaping spaces:
     ```bash
     mv file\ name.txt
     ```
     or
     ```bash
     mv "file name.txt"
     ```

2. **Dollar Sign (`$`):**
   - The dollar sign is used for variable substitution. If you have `$` in a file name, it must be escaped.
   ```bash
   touch \$file.txt
   ```

3. **Asterisk (`*`):**
   - `*` is a wildcard character used to match multiple files. To handle a file that contains an asterisk, escape it:
   ```bash
   touch file\*.txt
   ```

4. **Ampersand (`&`):**
   - The ampersand runs commands in the background. Escaping it ensures it’s treated as part of the file name:
   ```bash
   touch file\&name.txt
   ```

5. **Parentheses (`(` and `)`):**
   - Parentheses are used for grouping commands. To use them in file names, escape them:
   ```bash
   touch file\(test\).txt
   ```

6. **Single Quote (`'`):**
   - Single quotes inside file names can be tricky. Escape each individual quote:
   ```bash
   touch file\'s_name.txt
   ```

7. **Exclamation Mark (`!`):**
   - The exclamation mark is used for command history. Escape it:
   ```bash
   touch file\!.txt
   ```

8. **Backslash (`\`):**
   - The backslash itself is an escape character, so you need to escape it when used in file names:
   ```bash
   touch file\\name.txt
   ```

### Summary:
- Special characters in Unix file names may need to be **escaped** using backslashes (`\`), single quotes (`' '`), or double quotes (`" "`).
- The most common characters that require escaping include spaces, `$`, `*`, `&`, `!`, and `()`.
- Understanding how to escape characters ensures that file names are correctly interpreted by the shell.


---


## Coffee break!

![](https://m.media-amazon.com/images/I/517VAiwmYHL._AC_SL1200_.jpg)

Let's now stop for 15 minutes  for a comfort and coffee break.
While slurping, ask ChatGPT to give you a joke based on `mkdir`.


---

## Moving around
On Unix-like systems, files and directories are managed in a hierarchical structure, where files and directories sit within folders, which in turn can in turn sit within directories higher up in the hierarchy.

To find out where you are in the hierarchy use the `pwd ` command, which stands for "print working directory"

```bash
$ pwd

```
The result will look something like this.

```bash
/Users/username/Desktop/bioinfo_adventures/bioinfo_fun

```
The forward slashes list the directories down from the topmost directory, which is called the `root` directory.

Every location (file or directory) in the file system can be described either:

- as an `absolute path`, that is the full path from the root directory to the location,

    - for example
  
```bash
/users/admin/steve
```
  
- as a `relative path`, that is the path from the current directory to the location, so if we are inside the directory called `admin`, the path to the same directory would be

```bash
$ steve
```
  
---

## Absolute and Relative Paths
Let's clarify these concepts:

**Absolute paths** (almost) always start with `/`, and they are the same for everyone, no matter where they are in the file system. 

 - Each absolute path is crafted separating with slashes the names of the directories in the path. The final trailing slash (for directories) is optional, but it's wrong if the path is for a file.

- This is an absolute path for a directory
  
```bash
/users/admin/steve
```


- This is an absolute path for a file
 
```bash
/users/admin/list.txt
```

 
**Relative paths** never start with `/` and they are different depending on where they are in the file system.

 - Your current directory is represented by the dot `.`
 - The parent directory is represented by `..`
 - Example: this means that you want to access a file inside a directory that is two levels above your current directory

```bash
../../directory/file.txt
```

Remember that if you don't know where you are, you can always use `pwd` to print the current directory (its output is an absolute path).


:question: **TASK:** How can you move to the parent directory of your current folder? 

Type that command now.

Note that how `cd` can take an absolute or relative path as a parameter. 

If you type `cd` on its own it takes you to your home directory. 

If you want to return to your previous directory, you can use `cd -`
This a very useful feature that allows you to quickly switch between your current directory and the last directory you were working in. It is especially helpful when you need to jump back and forth between two directories without manually typing long paths every time. Here’s how it works:
   - When you change directories using `cd` <directory_path>, your previous working directory is stored in memory.
Using the `cd -` command, you can return to this previous directory.
If you use `cd -`  again, you will go back to the directory you originally came from.

  
As noted, the tilde character `~` is a shortcut for the home directory of the current user, so if "Steve" is the active user, the home directory is ` /users/admin/steve ` which can be written as `~ `, so Steve can also `cd` to their home directory with

```bash
$ cd ~
```

---



**Unix nerd joke**: 
Q. What did Dorothy say at the end of her first Unix tutorial?
A. There's no place like ~


---



### Listing files

If we want to find out what is inside a directory we use the `ls` command (short for "list")

```bash
$ ls

```
Sometimes files and directories are hidden from us by the operating system, usually if they start with a dot. To reveal all the files, we apply the flag `-a` to the command that alters its behaviour to list all files and directories. This a typical thing to do with Unix commands, where the flags are usually one or two characters prefaced by a dash.

```bash
$ ls -a
```

```bash
$ . .. bioinfo fun bioinfo_fun grandeur.txt
```

In this case, it reveals shortcuts to the directory above with two dots `..` and a single dot `.`, which is a shortcut referring to the current directory.

If you specify a directory, the `ls` command will list the contents of that directory.

```bash
$ ls ~/Desktop

```

- Tip: if your screen gets cluttered with outputs of previous commands, type `clear` to clear it up

```bash
$ clear

```

## Finding help when using a command

Many core bash commands have an entry in the manual that gives a detailed description of the command and its optional flags.

To view the manual entry for a function type:

```bash
man ls
```

Not all commands will have a manual entry, but every command should return some description of its use if you pass the help flag to the command.

```bash
ls -h
ls --help
``` 

Never be embarrassed to just type the command into google and see what people say on sites like Stack Overflow. We do it all the time!

:question: **TASK:** How do you list additional information about files in a folder such as the owner, the number of bytes in the file and when file was last modified?

---

### Time for lunch

![](https://upload.wikimedia.org/wikipedia/commons/1/1d/Sudo_logo.png)



---



How about a few Unix in-jokes to end this session

Which command do Unix files hate to play hide-and-seek with?

- `ls`, because it always finds out where they are and what they have permission to do

Why bioinformatics students always feel nostalgic?

- Because every time they feel lost, they'd just cd ~ and find themselves back home.



---


A few silly commands for you to try:

```bash
$ yes you_must_stop_this_using_Ctrl_Z
```

```bash
$ Say I hate Unix already, let me out of here
```


---



You say you already hate Unix??

Take a look at this old classic, which has a good moan about many aspects of Unix: 

 - [![The Unix-Haters Handbook](https://upload.wikimedia.org/wikipedia/en/7/77/UNIX-HATERS_Handbook_cover_ISBN_1-56884-203-1.png)](https://web.mit.edu/~simsong/www/ugh.pdf)



Or this track:
- [Everybody hates Linux](https://www.youtube.com/watch?v=lb2MOSCJIw8)

A few quotes on Unix:
- "UNIX was not designed to stop you from doing stupid things, because that would also stop you from doing clever things."
- "Unix is user-friendly. It's just picky about who its friends are."



---


