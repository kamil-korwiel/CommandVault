# sed
Is a stream editor 
#file
#text
#editor 

---
Delimiter - (pl: Separator)  /../../
```bash
/../../ # sed 's/from this/to this/' file.txt 
:..:..: # sed 's:from this:to this:' file.txt 
_.._.._ # sed 's_from this_to this_' file.txt 
|..|..| # sed 's|from this|to this|' file.txt 
```
---
` s ` - substitute 
` g `  - general or global
` i ` - ignore case sensitivities 
```bash
sed 's/from this/to this/' file.txt #one first instace in line
sed 's/from this/to this/2' file.txt #one second instace in line
sed 's/from this/to this/g' file.txt #all instance in line 
sed 's/from this/to this/2g' file.txt #all instance in line with out second

```
---
` a ` - append
` i ` - insert
` c ` - change / replace line
```bash
sed '1a bebebbe' file.txt #after line 1 will be added a text 'bebebbe'
sed '1i bla bla' file.txt #in line 1 will be added text 'bla bla'
sed '1c eeeeeee' file.txt #in line 1 text will be replace with 'eeeeeee'

sed '/Pattern/ i words to insert' file.txt
```
---
`&`  - mach element that  can be used in replace / substitute marching
`\1` - representation of the firs group expression 
`\2` -  representation of the second group expression

###### Printing
n - suppress automatic printing a found pattern 
` $ ` - last line 
` p ` - printing 
` = ` - 
```bash
sed -n 'p' file.txt  # print all line
sed -n '1p' file.txt # print first line 
sed -n '5,10 p' file.txt # print 5 line to 10 line
sed -n '24,$ p' file.txt # print 24 line to the end of file
sed -n '5,$ !p' file.txt # print all but not line 5
sed -n '1~4 !p' file.txt # every fourth line print line start 1 
sed -n '/finding/, +2p' file.txt


sed '=' file.txt # print only a number line with text line
sed -n '=' file.txt # print only number line of text

```



Deleting all lines that start with a "#" is easy:
```bash
sed '/^#/ d'
```

Removing comments and blank lines takes two commands. The first removes every character from the "#" to the end of the line, and the second deletes all blank lines:
```bash
sed -e 's/#.*//' -e '/^$/ d'
```

A third one should be added to remove all blanks and tabs immediately before the end of line:
```bash
sed -e 's/#.*//' -e 's/[ ^I]*$//' -e '/^$/ d'
```


| Sed                           | Range | Command | Results                                             |
| ----------------------------- | ----- | ------- | --------------------------------------------------- |
| sed -n                        | 1,10  | p       | Print first 10 lines                                |
| sed -n                        | 11,$  | !p      | Print first 10 lines                                |
| sed                           | 1,10  | !d      | Print first 10 lines                                |
| sed                           | 11,$  | d       | Print first 10 lines                                |
| ----------------------------- | ----- | ------- | --------------------------------------------------- |
| sed -n                        | 1,10  | !p      | Print last 10 lines of my 20-line file              |
| sed -n                        | 11,$  | p       | Print last 10 lines of my 20-line file              |
| sed                           | 1,10  | d       | Print last 10 lines of my 20-line file              |
| sed                           | 11,$  | !d      | Print last 10 lines of my 20-line file              |
| ----------------------------- | ----- | ------- | --------------------------------------------------- |
| sed -n                        | 1,10  | d       | Nothing printed                                     |
| sed -n                        | 1,10  | !d      | Nothing printed                                     |
| sed -n                        | 11,$  | d       | Nothing printed                                     |
| sed -n                        | 11,$  | !d      | Nothing printed                                     |
| ----------------------------- | ----- | ------- | --------------------------------------------------- |
| sed                           | 1,10  | p       | Print first 10 lines twice, then next 10 lines once |
| sed                           | 11,$  | !p      | Print first 10 lines twice, then last 10 lines once |
| sed                           | 1,10  | !p      | Print first 10 lines once, then last 10 lines twice |
| sed                           | 11,$  | p       | Print first 10 lines once, then last 10 lines twice |

