# Command Challenge

## **Print “hello world” on the terminal in a single command.**

```
> echo “hello world”
```



## **Print the current working directory.**

```
> pwd
```



## **List names of all the files in the current directory, one file per line.**

```
> ls
```



## **There is a file named access.log in the current directory. Print the contents.**

```
> cat access.log
```



## **Print the last 5 lines of “access.log”.**

```
> tail -5 access.log
```



## **Create an empty file named take-the-command-challenge in the current working directory.**

```
> touch take-the-command-challenge
```



## **Create a directory named tmp/files in the current working directory**

```
> mkdir -p tmp/files
```



## **Copy the file named take-the-command-challenge to the directory tmp/files**

```
> cp take-the-command-challenge ./tmp/files/
```



## **Move the file named take-the-command-challenge to the directory tmp/files.**

```
> mv take-the-command-challenge ./tmp/files/
```



## **Create a symbolic link named take-the-command-challenge that points to the file tmp/files/take-the-command-challenge.**

```
> ln -s tmp/files/take-the-command-challenge
```



## **Delete all of the files in this challenge directory including all subdirectories and their contents.**

```
> rm -r * .*
```



**There are files in this challenge with different file extensions.**\
**Remove all files with the .doc extension recursively in the current working directory.**
------------------------------------------------------------------------------------------

```
> rm -r **/*.doc
```



## **There is a file named `access.log` in the current working directory. Print all lines in this file that contains the string "GET".**

```
> grep "GET" access.log
```



## **Print all files in the current directory, one per line (not the path, just the filename) that contain the string “500”.**

```
>  grep -l "500" *
```



## **Print the relative file paths, one path per line for all filenames that start with “access.log” in the current directory.**

```
> ls *access.log*
```



## **Print all matching lines (without the filename or the file path) in all files under the current directory that start with “access.log” that contain the string “500”.**

```
> grep -rh "500"
```



## **Extract all IP addresses from files that start with “access.log” printing one IP address per line.**

```
> grep -ro ^[0-9.]*
```



## **Count the number of files in the current working directory. Print the number of files as a single integer.**

```
> ls -A | wc -l 
```



## **Print the contents of access.log sorted.**

```
> cat access.log | sort 
```



## **Print the number of lines in access.log that contain the string “GET”.**

```
> grep "GET" access.log | wc -l
```



## **The file split-me.txt contains a list of numbers separated by a `;` character. Split the numbers on the `;` character, one number per line.**

```
> cat split-me.txt |tr ';' "\n"
```



## **Print the numbers 1 to 100 separated by spaces.**

```
> echo {1..100};
```



## **This challenge has text files (with a .txt extension) that contain the phrase “challenges are difficult”. Delete this phrase from all text files recursively.**

```
> sed -i "challenges are difficult" **/*.txt
```



## **The file sum-me.txt has a list of numbers, one per line. Print the sum of these numbers.**

```
> cat sum-me.txt|paste -sd+|bc
```



## **Print all files in the current directory recursively without the leading directory path.**

```
> find -type f -printf  "%f\n"
```



## **Rename all files removing the extension from them in the current directory recursively.**

```
> rm -rf *
```



## **The files in this challenge contain spaces. List all of the files (filenames only) in the current directory but replace all spaces with a ‘.’ character.**

```
> ls | tr ' ' '.'
```



## **In this challenge there are some directories containing files with different extensions. Print all directories, one per line without duplicates that contain one or more files with a “.tf” extension.**

```
> dirname **/*.tf | sort -u
```



## **There are a mix of files in this directory that start with letters and numbers. Print the filenames (just the filenames) of all files that start with a number recursively in the current directory.**

```
> find -type f -printf '%f\n' | grep ^[0-9]
```



## **Print the 25th line of the file faces.txt**

```
> head -25 faces.txt | tail -1
```



## **Print the lines of the file `reverse-me.txt` in this directory in reverse line order so that the last line is printed first and the first line is printed last.**

```
> tac reverse-me.txt
```



## **Print the file faces.txt, but only print the first instance of each duplicate line, even if the duplicates don’t appear next to each other.**

```
> cat -n faces.txt | sort -u -k 2 | sort -n | cut -f 2
```



**The file random-numbers.txt contains a list of 100 random integers.**\
**Print the number of unique prime numbers contained in the file.**
-------------------------------------------------------------------

```
> cat random-numbers.txt | sort | uniq | factor | awk "NF==2" | wc -l
```



## **access.log.1 and access.log.2 are http server logs. Print the IP addresses common to both files, one per line.**

```
> awk 'a[$1]++ {print $1}' {access.log.1,access.log.2}
```



## **Print all matching lines (without the filename or the file path) in all files under the current directory that start with “access.log”, where the next line contains the string “404”.**

```
> grep -h -B1 404 **/access.log* | grep -vE '404|--'
```



## **Print all files with a `.bin` extension in the current directory that are different than the file named base.bin.**

```
> diff *.bin --to-file=base.bin | cut -d ' ' -f3
```



## **There is a file: `./.../ /. .the flag.txt` Show its contents on the screen.**

```
> cat './.../  /. .the flag.txt'
```



## **How many lines contain tab characters in the file named `file-with-tabs.txt` in the current directory.**

```
> grep -P "\t" * | wc -l
```



## **There are files in this challenge with different file extensions. Remove all files without the .txt and .exe extensions recursively in the current working directory.**

```
> find -type f ! -regex '.*\(exe\|txt\)$' -delete
```



## **There are some files in this directory that start with a dash in the filename. Remove those files.**

```
> rm ./-*
```



## **There are two files in this directory, ps-ef1 and ps-ef2. Print the contents of both files sorted by PID and delete repeated lines.**

```
> cat ps-* | sort -k2 -n | uniq
```



## **In the current directory there is a file called netstat.out. Print all the IPv4 listening ports sorted from the higher to lower.**

```
> cat netstat.out | grep -w "LISTEN" | awk '{print $4}' | cut -d":" -f2 |  sort -rn
```
