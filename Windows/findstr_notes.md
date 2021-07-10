# findstr examples

+ Search for string "tralala" in all .java files in current folder and all subfolders (/s flag). Case insensitive (/i flag). Redirect results to output file.
```
findstr /s /i tralala *.java > c:\temp\search_results.out
```

-----------------------------

+ Search every file in current folder and all subfolders for the word "Smith", case insensitive. Print also matching line number.
```
findstr /n /s /i smith *.*
```

-----------------------------

+ Search for "granny" OR "Smith" in files Apples.txt and Pears.txt
```
findstr "granny Smith" Apples.txt Pears.txt 
```

-----------------------------

+ Search for "granny Smith" in Contacts.out
```
findstr /c:"granny Smith" Contacts.out
```

-----------------------------

+ Use regex (/r flag) to search for lines containing both "hello" and "goodbye" in any order. Search all .log files in current folder and all subfolders. Case insensitive.
```
findstr /s /i /r /c:"hello.*goodbye" /c:"goodbye.*hello" *.log
```
