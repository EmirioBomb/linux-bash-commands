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
---
#### Directories

##### 1. ls
> list directory contents

``` bash
1. list in long format, the most common used combined by other arguments
$ ls -l

-> list entries with a slash ('/') after file name if that file is a directory
$ ls -p
$ ls -lp

-> recursively list subdirectories  
$ ls -R

2. list include directory entries whose names begin with a dot (.)
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
> change directory

``` bash
1. change to basic directory
-> change to user home directory
$ cd
$ cd ~

-> change directory by absolute or relative path
$ cd .
$ cd ..

2. navigate to the previous directory
** (-) will print working directory with relative path **
$ cd -

-> example: 
$ cd ../user/lib/xxx
$ cd ~
$ cd -
```

