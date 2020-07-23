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
$ du -s <folder_name>
equivalent to -d 0
$ du -d 0 <folder_name>

3. display the disk usage of all files
$ du -sh <folder_name>
equivalent to 
$ du -d 0 -h <folder_name>

4. calculate and display disk usages, but excludes the files that matches given pattern
$ du -ah --exclude=".txt" <folder_name>

5. display an entry for all files and directories depth dirctories deep
$ du -d <number>    # if number is big enough, then it's euqal to du -h
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

