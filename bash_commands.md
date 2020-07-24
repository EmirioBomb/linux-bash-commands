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
