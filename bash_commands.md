## Linux Bash Commands

#### File Examination

##### 1. cat
> concatenate and print files

``` bash
1. number the output lines, starting at 1
$ cat -n file1 file2 ... fileN

** (-b) will override (-n) options **

2. number the non-blank lines, starting at 1
$ cat -b file1 file2 ... fileN

-> print sequentially to the file3 with line number
$ cat -b file1 file2 > file3

3. print file1 ... fileN to the screen
$ cat file1 file2 file3 ... fileN

4. print sequentially file1 and file2 to the file3, if it already exists
$ cat file1 file2 > file3
$ cat file1 file2 ... fileN > fileN1

5. squeeze multiple adjacent empty lines, cause the output to be single spaced
$ cat -s file

-> check (-s) result
$ cat -sb file
or 
$ cat -sn file

6. create a new file with (<)
$ cat < file
$ ctrl + z
```

##### 2. more / less
> display contents of a file, one page at a time

```bash
1. display text after the specified line number
$ more / less +n file   # n means line number

2. show with line number
$ more / less -N file

3. squeeze multiple adjacent empty lines
$ more / less -s file
```

##### 3. head / tail
> dislpay the beginning or ending of a file

``` bash
1. display first / last lines of a file
$ head -n <count>   # count means number
$ tail -n <count>   # count means number

2. display number bytes of a file
$ head -c <number>
$ tail -c <number>

3. tail vs head
# '+<count> means starts the display at the <count> byte of the input'
$ tail -c +<count>

# '+<count> means starts the display at the <count> line of the input'
$ tail -n +<count>
```

##### 4. wc
> word, byte, line, character count

``` bash
1. count the number of words, not character
$ wc -w file1 file2  ...

2. count the number of bytes
$ wc -c file1 file2 ...

3. count the number of lines
$ wc -l file1 file2 ...

4. combine all
# default order: 
$ wc -mclw file1 file2 ...
```

##### 5. du
> display disk usage statistics

``` bash
1. human-readable ouput, use unit sufiixes: Byte, Kilobyte, MegaByte, Gigabyte, Terabyte, Petabyte
$ du -h file1 file2 ...

2. display an entry for each specified file
$ du -s <dir_name>
equivalent to -d 0
$ du -d 0 <dir_name>

3. display the disk usage of all files
$ du -sh <dir_name>
equivalent to 
$ du -d 0 -h <dir_name>

4. calculate and display disk usages, but excludes the files that matches given pattern
$ du -ah --exclude=".txt" <dir_name>

5. display an entry for all files and directories depth dirctories deep
$ du -d <number>    # if number is big enough, then it's euqal to du -h
```

##### 6. diff
> compare files line by line

``` bash
1. output in two columns
$ diff -y file1 file2

2. ignore case differences in file contents
$ diff -i / --ignore-case file1 file2

3. ignore case whent comparing file names
$ diff --ignore-file-name-case file1 file2

4. output only whether files differ
$ diff -q file1 file2

5. [OPTIONS]
-E: ignore changes due to tab expansion
-b: ignore changes in the amount of white space
-w: ignore all white space
-B; ignore changes whose lines are all blank
```

---
#### Directories

##### 1. ls
> list dir contents

``` bash
1. list in long format, the most common used combined by other arguments
$ ls -l

-> list entries with a slash ('/') after file name if that file is a dir
$ ls -p
$ ls -lp

-> recursively list subdirectories  
$ ls -R

2. list include dir entries whose names begin with a dot (.)
$ ls -a

3. list all entries except for (.) and (..)
$ ls -A

4. list entries or files sort by size (default by decreasing size)
$ ls -lS

-> sort by increasing size
$ ls -lrS

-> sort by time modified (most recently modified first)
$ ls -lt

-> sort by time with complete time information
$ ls -lTt

5. list entries with unit suffixes: Byte, Kilobyte, Megabyte, Gigabyte, Terabyte, Petabyte
$ ls -lh
```

##### 2. cd
> change dir

``` bash
1. change to basic dir
-> change to user home dir
$ cd
$ cd ~

-> change dir by absolute or relative path
$ cd .
$ cd ..

2. navigate to the previous dir
** (-) will print working dir with relative path **
$ cd -

-> example: 
$ cd ../user/lib/xxx
$ cd ~
$ cd -
```

##### 3. pwd
> print working dir name

``` bash
1. print logical current working dir name
$ pwd
```

##### 4. mkdir
> make dirctories

``` bash
1. create intermediate directories as required
# if -p is not specified, directory must exist
$ mkdir -p dir1/dir2/...

2. create dirctory with the specified mode 
$ mkdir -m 777  # 777 means 'rwxrwxrwx'
```

##### 5. rmdir
> remove directories

``` bash
1. remove empty directory
# directory must be empty
$ rmdir dir

2. remove empty direcotries recursively
# directory must be empty
$ rmdir dir1/dir2/dir...

3. remove (-filename) which created by (mkdir -p -filename)
$ rmdir -- -filename    # -- will stop processing option flag at this point
```

---
#### File Operations

##### 1. cp
> copy files

``` bash
1. preserves structure and attributes of files but not directory structure
$ cp -a source_file target_file
or 
$ cp -pPR source_file target_file

2. do not overwrite an existing file (-n option overrides any previous  -f -r)
$ cp -n source_file target_file

3. prompt to the standard error output before copying a file
$ cp -i source_file target_file

4. if the destination file cannot be opened, remove it and create a new file
$ cp -f source_file target_file

5. recursive copy files, include hidden files
$ cp -R source_file target_file

6. copy multi files to directory which cannot be empty
$ cp file1 file2 ... directory
```

##### 2. mv
> move or rename files or directory

``` bash
1. do not prompt for comfirmation before overwriting the destination path
$ mv -f source target

2. prompt to the standart ouput before moving a file or directory
$ mv -i source target

3. do not overwrite an existing file or directory
$ mv -n source target

4. move multi files to a directory that cannot be empty
$ mv [-fin] file1 file2 ... dir

5. rename file or directory name
$ mv [-fin] source_file target_file
```

##### 3. rm
> remove files or directories

``` bash
1. attempt to remove directories as well as other types of files
$ rm -d file1 file2 ...
or
# if directory is not empty, failed to remove directory
$ rm -d dir1 dir2 ...

2. recursive remove files or directories (-r is equal to -R)
$ rm -r[-R] dir1/dir2/file

-> extend
# remove files without prompt
$ rm -rf[-Rf] dir1/dir2/file1 file2

# remove files with interactive prompt
$ rm -ri[-Ri] dir1/dir2/file1 file2

3. remove file start with (-) which created by (mkdir -p -filename)
$ rm -- -filename   # -- option will stop processing flag options at this point
```

##### 4. touch
> change file access and modification times

``` bash
1. do not create file if it exists with no error messages 
$ touch -c file     # file has already exist

2. creat a new file if it does not exist
$ touch file
```

---
#### File Permissions

##### 1. chmod
> chang file modes or access control lists

``` bash
# read      -> open for reading
# write     -> open for writing
# append    -> open for writing, but in a fashion that only allows writes into areas of the file not previously writtern
# rwx+      -> + means append
# execute   -> execute file as a script or program

# user    group   other
# rwx      rwx     rwx

1. set permission with number
$ chmod 644 file

-> examples
$ chmod 1 file      # --------x file
$ chmod 11 file     # -----x--x file
$ chmod 400 file    # r-------- file

2. set permissiion with u(user) g(group) o(other)
$ chmod u+r g-x o+w file    # user add read, group remove execute, others add write mode
$ chmod ugo-r   # remove read permission for user/group/others

3. add append info and check append info
$ chmod +a 'guest deny read' file
$ ls -le file

4. set read and write permissions to the usual defaults, but retain any execute permissions that are currently set
$ chmod =rw,+X file
```

##### 2. chown
> change files owner and group

``` bash
1. recursive change user id or group id for the hierachies rooted in the files
$ chown -R <userid> file/directory
```

##### 3. chgrp
> change group

``` bash
1. recursive change group for the hierachies rooted in the files
$ chgrp -R <group-id> file/directory
```

##### 4. umask
> change the default permissions given to newly created directories or files

``` bash
1. check current default permissions
$ umask -S

2. set default permission
# Note that when the mode is interpreted as an octal number, each number of the umask is subtracted from 7. Thus, a umask of 022 results in permissions of 755.
$ umask 022
```

---
#### System Informations

##### 1. date
> display or set date and time

``` bash
1. display default date
$ date  # default is CST format

2. display date with UTC format
$ date -u

3. display filename date
$ date -r filename 
or 
$ date -ur filename     # option must be [-ur], [-ru] is incorrect

4. display time format
$ date "+DATE: %Y-%m-%d%nTIME: %H:%M:%S" 
```

##### 2. cal
> display a calendar

``` bash
1. display calendar
$ cal

2. turns off highlighting of today
$ cal -h

3. display the previous, current and next month surrounding today
$ cal -3

4. display the number of the month after the current month
$ cal -A <number>   # number = 1......N

5. display the number of the month before the current month
$ cal -B <number>   # number = 1......N

6. display a calendar of the specified year
$ cal -y <year>
```

##### 3. uname
> print operting system name

``` bash
1. print operating system version
$ uname -v

2. print machine processor architecture name
$ uname -p

3. print machine hardware name
$ uname -m

4. print operating system release
$ uname -r

5. print operating system name
$ uname -s

6. print the nodename for communication network 
$ uname -n

7. [-a] behave as though all of the options -mnrsv were specified
$ uname -a
```

##### 4. time
> time command execution

``` bash
1. measure the time taken to download files using the wget tool
$ time wget https://cdn.kernel.org/pub/linux/kernel/v4.x/linux-4.19.9.tar.xz
```

---
#### Users and Groups

##### 1. whoami
> display effective user id

``` bash 
1. display effective user id
$ whoami
```

##### 2. passwd
> modify a user's password

``` bash
1. modify user's password
$ passwd <username>
```

##### 3. groups
> show group memberships

``` bash
1. show groups memberships
$ groups <username>
```

##### 4. su
> substitute user identity

``` bash
1. sustitute user
$ su user

2. simulate a full login, su will change dirctory to the target's home directory
$ su -l user
same as 
$ su - user
```

##### 5. sudo
> execute a command as another user

``` bash
1. substitute root
$ sudo su   # compatible with MACOS

2. edit file as user root
$ sudo -u root vim filename

3. to get a file listing of an unreadable directory
$ sudo ls -l /usr/local/protected
```

---
#### Searching and Sorting

##### 1. grep
> grep = (global search regular expression) file pattern searcher

``` bash
1. to find all occurrences of the word 'test' in a file or files
$ grep 'test' filename
$ grep 'test' file1 file2 ... fileN

2. to find all occurrences of the pattern '.txt' in a file or files
$ grep '^\.txt' filename
$ grep '^\.txt' file1 file2 ... fileN

3. to find all lines in a file which do not contain the words 'foo' and 'bar'
$ grep -v -e 'foo' -e 'bar' filename

4. display line number counter
$ grep -n 'xxx' file

5. display couter of selected lines
$ grep -c 'xxx' file

6. always print filename headers with output lines
$ grep -H 'xxx' file

7. recursively search subdirectories listed
$ grep -R / -r directory

8. specify a pattern
$ grep -e "[1-9]+"

9. begin with 'd', end with 'x'
$ grep '^d' filename
or
$ grep 'x$' filename
```

##### 2. find
> walk a file hirerarchy

``` bash
1. find "a.txt" files in the specified directories
$ find ./ -name 'a.txt'

2. same as above, but ignore case sensitive
$ find ./ -iname 'a.txt'

3. print out a list of all the files whose names do not end in .txt
$ find . \! -name '*.txt' -print    # print can be ignored

4. find file by the specified type, possible file types are as follows
# b -> block special
# c -> character special
# d -> directory
# f -> regular file
# l -> symbolic link
# p -> FIFO
# s -> socket
$ find -type f 'a.txt' 

5. find file whose size is in a specified size, scale indicators are like (c(byte) / k(bytes) / M(Megabyte) / G(Gigabyte) / T(Terabyte) / P(Petabyte))
$ find . -type f -size 10c  # 10c -> 10bytes
# +10c -> larger than 10bytes
# -10c -> smaller than 10bytes
# 10c -> equal to 10bytes

6. find files with other utilities
$ find . -type f -size 10c -exec ls -lSh {} \;
```

##### 3. locate
> find filenames quickly

``` bash
1. locate files that begin with "sh"
$ locate /usr/lib/sh
```

##### 4. which
> locate a program file in the user's path

``` bash
1. which git
# /usr/bin/git
```

##### 5. sort
> sort or merge records of text and binary files

``` bash
1. sort lines
# a.txt -> 2. this is the first line
# b.txt -> 1. this is the second line
# c.txt -> 0. this is header line
$ sort a.txt b.txt

2. print the output to the output file
$ sort file1 file2 ... fileN -o output_file

3. suppress all lines that have a key that is equal to an already processed one.
# file1 -> 1. this is the first line
#       -> 1. thiis is the xxx
#       -> 1. this is the first line
$ sort -u file1
# 1. this is the first line
# 1. thiis is the xxx
```

---
#### Process Management

##### 1. ps
> process status

``` bash
1. show all current running process
$ ps -ax

2. search for a particular process
$ ps -ef | grep iterm

3. show all processes with BSD format
$ ps -axu username  # -u must added to tail
```

##### 2. jobs
> display status of jobs in the current session

``` bash
# ctrl(^) + z suspends current running process
1. show suspended jobs
$ jobs -l
or
$ jobs -p   # show pid
or 
$ jobs  # with no option means displaying jobs with no pid

2. show running jobs only
$ jobs -r

3. show sotpped jobs only
$ jobs -s
```

##### 3. bg / & / fg
> list the jobs running in the background

``` bash
1. running the current jobs in the background with specified jobs_id
$ bg %N     # N means jobs identifier

-> running the current jobs in the background with specified jobs_name
# bg %?String
# example: [1]- stopped nautilus
#          [2]+ sotpped beautilus
# + - means last or 
$ bg %?ti   # it will run beautilus in the background

2. running the current jobs in the foreground
$ fg %N     # N means jobs identifier

-> running the current jobs in the foreground with specified jobs_name
# as same as above
$ fg %?ti   # it will run beautilus in the foreground

3. running the current jobs in the background
# close current session, if you want to kill or stop job with &
$ ping baidu.com &  # running in the background

4. running the previous jobs in the back/foreground
$ bg / fg %%
or 
$ bg / fg %+

5. running the last jobs in the back/foreground
$ bg / fg %-
```

##### 4. top
> display and update sorted information about processees

``` bash
1. only display up to N processes
$ top -n N  # N means number

2. sort the processes by cpu usage (decending) and display up to 10 processes
$ top -o cpu -n 10  # order by cpu
$ top -o mem        # order by memory usage

3. display only the specified statistics, regardless of any growth of the terminal
$ top -stats pid,uid,cpu,mem,time

4. display with pid
# ps -ef | grep process_name
$ top -pid porcess_id
```

##### 5. kill
> terminate a signal or process

``` bash
# commonly used singals
# 1. HUP    -> hang up
# 2. INT    -> interrupt
# 3. QUIT   -> quit
# 6. ABRT   -> abort
# 9. KILL   -> non-catchable, non-ignorable kill
# 14 ALRM   -> alarm clock
# 15 TERM   -> software termination signal
1. terminate processes with PIDs 142 and 157
$ kill 142 157

2. send the signal to the process with pid 157
$ kill -s HUP 157
or 
$ kill 1 157
```

##### 6. killall
> kill processes by name

``` bash
1. list the names of the available signals and exit
$ killall -l

2. kill two prcesses or more at once
$ killall process1 process2 ... process3
```