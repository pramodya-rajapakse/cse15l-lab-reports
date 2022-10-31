# Lab Report 3
## Less Commands
The less command in its simplest form is meant to display the contents of a file one page at a time in the terminal. The user can go through the document either line by line, or by page, making it easier to see all the contents of a file, especially if it is long. Since the text takes up the entire command line window, the user needs to enter "q" to exit the text.
For example, in the **technical/911report** directory, using the command `less chapter-1.txt` will result in the following output
```
"WE HAVE SOME PLANES"

    Tuesday, September 11, 2001, dawned temperate and nearly cloudless in the eastern United States. Millions of men and women readied themselves for work. Some made their way to the Twin Towers, the signature structures of the World Trade Center complex in New York City. Others went to Arlington, Virginia, to the Pentagon. Across the Potomac River, the United States Congress was back in session. At the other end of Pennsylvania Avenue, people began to line up for a White House tour. In Sarasota, Florida, President George W. Bush went for an early morning run.

    For those heading to an airport, weather conditions could not have been better for a safe and pleasant journey. Among the travelers were Mohamed Atta and Abdul Aziz al Omari, who arrived at the airport in Portland, Maine.

INSIDE THE FOUR FLIGHTS

Boarding the Flights

    Boston: American 11 and United 175. Atta and Omari boarded a 6:00 A.M. flight from Portland to Boston's Logan International Airport.

    When he checked in for his flight to Boston, Atta was selected by a computerized prescreening system known as CAPPS (Computer Assisted Passenger Prescreening System), created to identify passengers who should be subject to special security measures. Under security rules in place at the time, the only consequence of Atta's selection by CAPPS was that his checked bags were held off the plane until it was confirmed that he had boarded the aircraft. This did not hinder Atta's plans.

:
```
As we can see, the contents of **chapter-1.txt** is displayed in the command-line window, with the name of the file placed at the bottom, where you could enter "q" to exit this view. 
*Note: since the contents of these text files are very long, I will only include a short section of them relevant to the command.*
### less -p
Using the `-p` flag with the `less` command allows you to pass a string pattern, in which the command will display the given file starting from the first instance of the String provided. 
For example, if I used the command `less -p "Board" chapter-1.txt`, we get the following output:
```
Boarding the Flights

    Boston: American 11 and United 175. Atta and Omari boarded a 6:00 A.M. flight from Portland to Boston's Logan International Airport.

    When he checked in for his flight to Boston, Atta was selected by a computerized prescreening system known as CAPPS (Computer Assisted Passenger Prescreening System), created to identify passengers who should be subject to special security measures. Under security rules in place at the time, the only consequence of Atta's selection by CAPPS was that his checked bags were held off the plane until it was confirmed that he had boarded the aircraft. This did not hinder Atta's plans.

    Atta and Omari arrived in Boston at 6:45. Seven minutes later, Atta apparently took a call from Marwan al Shehhi, a longtime colleague who was at another terminal at Logan Airport. They spoke for three minutes.

    It would be their final conversation.

    Between 6:45 and 7:40, Atta and Omari, along with Satam al Suqami, Wail al Shehri, and Waleed al Shehri, checked in and boarded American Airlines Flight 11, bound for Los Angeles. The flight was scheduled to depart at 7:45.

    In another Logan terminal, Shehhi, joined by Fayez Banihammad, Mohand al Shehri, Ahmed al Ghamdi, and Hamza al Ghamdi, checked in for United Airlines Flight 175, also bound for Los Angeles. A couple of Shehhi's colleagues were obviously unused to travel; according to the United ticket agent, they had trouble understanding the standard security questions, and she had to go over them slowly until they gave the routine, reassuring answers.
```
As we can see, the contents of the file were displayed starting from the word "Boarding", which of course includes the string "Board". This could be very useful to someone wanting to see only a specific section of a very long file. By passing in a pattern of a section header or a known title, the user could easily start reading the file from a point they want, instead of having to manually scroll down to the desired section. 
If you entered a pattern that does not appear in the file, a message saying `Pattern not found` followed by a prompt to enter "Return" will displayed. Upon entering "Return", the user will be taken to the entirety of the file, as if only `less` was used.
### less -M
Using the `-M` flag causes the prompt at the bottom of the command line window when the file is opened to display additional information by default. For example, using the command `less -M chapter-1.txt` will result in the following output:
```
INSIDE THE FOUR FLIGHTS

Boarding the Flights

    Boston: American 11 and United 175. Atta and Omari boarded a 6:00 A.M. flight from Portland to Boston's Logan International Airport.

    When he checked in for his flight to Boston, Atta was selected by a computerized prescreening system known as CAPPS (Computer Assisted Passenger Prescreening System), created to identify passengers who should be subject to special security measures. Under security rules in place at the time, the only consequence of Atta's selection by CAPPS was that his checked bags were held off the plane until it was confirmed that he had boarded the aircraft. This did not hinder Atta's plans.

chapter-1.txt lines 1-17/731 1%
```
As we can see, it will show the exact lines that are being displayed in the current window, out of the total number of lines in the file, as well a percentage marking how far through the entire text file the user is currently at. This can be helpful if the user needs to quickly see which lines certain contents are at, or to find the contents if they are given line numbers. It also lets them know how far through the document they are using the percentage.
### "command" | less - piped input
The `less` command can also be used in a pipeline with other commands, especially ones that have some sort of important or extensive output. For example, when in the **technical/biomed** directory, using the command `ls | less`, you would get the following output:
```
...
1471-2091-3-16.txt
1471-2091-3-17.txt
1471-2091-3-18.txt
1471-2091-3-22.txt
1471-2091-3-23.txt
1471-2091-3-30.txt
1471-2091-3-31.txt
1471-2091-3-4.txt
1471-2091-3-8.txt
1471-2091-4-1.txt
1471-2091-4-5.txt
1471-2105-1-1.txt
1471-2105-2-1.txt
:
```
As we can see, it displayed the output of the `ls` command using less, making it much easier to search through the output of the command. This use of the `less` command could be very helpful if the user wanted to look through an output to a command that is very long, as is the case with `ls` on **biomed**, or if the user wanted to look through the ouput later. Perhaps if the user ran a command that does some kind of process, in which things are displayed and changed rapidly in the command line, they could look through the output later if needed to locate a particular element of it. 

---

## Find Commands
The `find` command on its own will find a file or directory name given a directory to search through. This command can be used to search for patterns of files, for example using `*.txt` to find all txt files in a given directory. 
One typical example is using the `-name` flag to search for a file or directory, like for example the command `find 911report -name "chapter-1.txt"` will result in the following ouput
```
911report/chapter-1.txt
```
As we can see, it found a file named "chapter-1.txt" in the **911report** directory, and printed its relative path added onto **911report**.
### find / -mtime
Using the `-mtime` flag with the find command allows you to find all the files in the given directory that have been modified within a given time. The time is passed by a flag with a number to denote the number of minutes, such as `-60`. For example, when in the **technical** directory, say I were to create a file called **911report/ch1.txt**, place some text in it, and then modify the existing file **911report/chapter-1.txt**. Then, if I ran the command `find 911report -name "*.txt*" -mtime -1`, I would get the following output:
```
911report/ch1.txt
911report/chapter-1.txt
```
As we can see, it displayed the relative paths of all the txt files that were modified within the last minute, denoted by the `-1` flag after `-mtime`. There are other options outside of `mtime`, like `ctime` which checks all files that were changed and `atime` which checks all files that were accessed. The `-mtime` command could be useful if you need want to see which files were modified within a time frame. Perhaps you want to check which files were modified before committing the changes, or maybe you want to see which files were modified after you ran a certain command. 
### find / -delete
The `-delete` flag could be used with the `find` command to delete the files you wanted to search for. The same expressions and flags could be used to locate files with a certain name or pattern in a directory, and then the `-delete` flag could be added onto to delete all the files and directories the command found. 
For example, in the **technical/911report** directory, there is a file named **ch1.txt**. When I use the command, `find 911report -name "*ch1.txt" -delete`, I will not recieve any output in the command line: 
```
```
However, after using this command, **technical/911report/ch1.txt** was removed, which I can verify from both `find 911report -name "*ch1.txt"` 
```
```
having no output, and by checking the contents of **technical/911report** using `cd 911report; ls`
```
chapter-1.txt    chapter-13.1.txt chapter-13.5.txt chapter-6.txt    preface.txt
chapter-10.txt   chapter-13.2.txt chapter-2.txt    chapter-7.txt
chapter-11.txt   chapter-13.3.txt chapter-3.txt    chapter-8.txt
chapter-12.txt   chapter-13.4.txt chapter-5.txt    chapter-9.txt
```
and seeing that ch1.txt is no longer there.
### find with operators
The `find` command could also be used with logical operators, NOT, AND, and OR to further get specific results using the command. For example, while in the **technical** directory, I could use the command `find 911report ! -name "chapter-1.txt"` resulting in the following output:
```
911report
911report/chapter-13.4.txt
911report/chapter-13.5.txt
911report/chapter-13.1.txt
911report/chapter-13.2.txt
911report/chapter-13.3.txt
911report/chapter-3.txt
911report/chapter-2.txt
911report/chapter-5.txt
911report/chapter-6.txt
911report/chapter-7.txt
911report/chapter-9.txt
911report/chapter-8.txt
911report/preface.txt
911report/chapter-12.txt
911report/chapter-10.txt
911report/chapter-11.txt
```
As we can see, it displayed all files and directories in **technical/911report** that didn't have the name "chapter-1.txt". In this case, the `!` was used as the NOT operator, and `-a` or `-and` performs an AND operation, and `-o` or `-or` would perform an OR operation. These operators can be very useful in trying to narrow down search results with more specific parameters. Instead of searching for one file type, you could search for all files that are not a specified file type  or types. Similarly, you could search for a file that has a specific name and is not a directory, using the `-type` flag. 

---
## Grep commands
The grep command can search through the contents of a file for a given pattern, such as string. For example, while in **technical/911report**, using the command `grep Board chapter-1.txt`, you would get the following output: 
```
Boarding the Flights
    United 93 crashed in Pennsylvania at 10:03:11, 125 miles from Washington, D.C. The precise crash time has been the subject of some dispute. The 10:03:11 impact time is supported by previous National Transportation Safety Board analysis and by evidence from the Commission staff 's analysis of radar, the flight data recorder, the cockpit voice recorder, infrared satellite data, and air traffic control transmissions.
```
As we can see, the command displayed the contents of "chapter-1.txt" showing each instance of the string "Board". The `grep` command by default will display every instance of the given pattern in the file provided.
### grep -w
Using the `-w` flag with the `grep` command allows you to search only for whole words of the pattern that was given as an argument. By default, the pattern that is given as a string will be searched for as a substring, so as long as it appears in some way it will be caught. While in the **technical/911report** directory, using the command `grep -w Board chapter-1.txt` has the following result:
```
United 93 crashed in Pennsylvania at 10:03:11, 125 miles from Washington, D.C. The precise crash time has been the subject of some dispute. The 10:03:11 impact time is supported by previous National Transportation Safety Board analysis and by evidence from the Commission staff 's analysis of radar, the flight data recorder, the cockpit voice recorder, infrared satellite data, and air traffic control transmissions.
```
As we can see, the text displayed is the section that has the word "Board", instead of previously in which the search started at the word "Boarding" since it contains the string "Board". The `-w` searches only for the whole use of the word. This can be helpful if you only want to search for instances of the specific word, excluding the times it appears as part of another word. 
### grep -c
Using the `-c` flag with the `grep` command doesn't displays the sections of the text that the pattern appears, but instead displays a count that had the number of times the pattern appeared from the `grep` command. While in the **technical/911report**, using the command `grep -c the chapter-1.txt` would result in the following output:
```
313
```
The command searches for each instance of the word "the" in the file **chapter1-txt**, which in this case is 313, and that number is displayed as the output. This can be useful if the user just wants to check how many instances of the pattern appearing in a file or files, without needing to see each instance within the file. Additionally, this number can then be used as input for other commands, such as through pipelining. 
### grep -l
Using the `-l` flag with the `grep` command lists all of the files in there is an instance of a given pattern of, if the command searches for more than one file. Using the command on one file will display only that file (assuming the pattern is in that file). For example, while in the **technical/911report**, running the command `grep -l Board *` will have the following output:
```
chapter-1.txt
chapter-11.txt
chapter-12.txt
chapter-13.2.txt
chapter-13.3.txt
chapter-13.5.txt
```
As we can see from the command, the `grep` command searches for the string "Board", within all files in the **911report** directory, as denoted by the `*` character. Using the `-l` flag lists all the files in which that pattern appears. This use can be very helpful if you only want to know which files contain the given pattern, especially if you want to use these files as input for another command (such as removing or moving all files in which the specified pattern appears).