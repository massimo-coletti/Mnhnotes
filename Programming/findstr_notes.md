# findstr examples

+ Search for string "tralala" in all .java files in current folder and all subfolders. Case insensitive. Redirect results to file.
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

+ Use regex to search for lines containing both "hello" and "goodbye" in any order. Case insensitive.
```
findstr /i /r /c:"hello.*goodbye" /c:"goodbye.*hello" somefile.log
```
