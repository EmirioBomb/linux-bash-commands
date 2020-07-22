## Linux Bash Commands

#### Basic

##### 1. cat
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
