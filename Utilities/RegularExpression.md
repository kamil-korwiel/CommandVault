# Regular Expression
for my need to understanding  regular expression I use "character =~ expectations =~ searching word " as some what equal  
symbol | description
--- | ---
 ``` () ``` | group the expressions 
``` [] ``` | bracket match like `[aA]` is some what similar to `(a\|A)`
` {} ` | this bracket say how many instance of character or expression ```{1,6}```  

###### Simple Us
` [DpsS] `  -  `D` or  `p` or `s` or `S`

###### Range
` [a-z] ` - all  lowercase letter
` [A-Z] ` - all uppercase letter 
` [0-9] ` - all numbers form 0 to 9

###### NOT
` [^Fg]ah ` - all 3 character words  that NOT start with `F` or `g` and and with  `ah`

###### Special characters
` . ` = representing all characters 

` ? ` = Match zero or one occurrences only.
` + ` = Match infinite occurrences of a character but never zero occurrences.
` * ` = Match zero, one or infinite occurrences.

` ^ ` = Start with ...
` $ ` = End with ...
` ^[a-z][0-9]$ ` - Start with a letter Ends with a number
` ^$ ` - Empty line


```bash
sed 's/[a-ż]*/&&/' 
```
