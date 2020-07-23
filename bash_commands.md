## Linux Bash Commands

#### Basic

##### 1. cat
> concatenate and print files

``` bash
1. number the output lines, starting at 1
$ cat -n file1 file2 ... fileN

2. number the non-blank lines, starting at 1
$ cat -b file1 file2 ... fileN

3. print file1 ... fileN to the screen
$ cat file1 file2 file3 ... fileN

4. print sequentially file1 and file2 to the file3, if it already exists
$ cat file1 file2 > file3
$ cat file1 file2 ... fileN > fileN1

5. print sequentially to the file3 with line number
$ cat -b file1 file2 > file3
```

##### 2. ls
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
