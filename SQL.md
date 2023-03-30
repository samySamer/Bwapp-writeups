### SQL Injection (POST/Select):
- So i started by trying to put \'  after the movies url so i can see what will happen
- and it gave me an error in sql syntax and that means that if i write sql it will work.
- So i tried union select in the url as follows:
``` url
`http://172.16.112.128/bWAPP/sqli_2.php?movie=1 and 1=0 union all select 1,2,3,4,5,6,7--&action=go`
```
- so i typed 1=0 as the union won't work if i didn't add it  as the first select will over write the second
- so when i tried that it returned all these numbers in the website in title release character and genre
- so i can now think of using instead of one of the numbers a user or something
- so when i used : 
```
http://192.168.56.101/bWAPP/sqli_2.php?movie=2%20and%201=0%20union%20all%20select%201,2,version(),user(),5,6,7--&action=go
```
- it returned instead of the release the version of the ubuntu and instead of the genre the user id :
  ![[Pasted image 20230329224307.png]]
---
### SQL Injection (Captcha):
- first i did was to get to the captcha as there was no tables or something like that
- then when i got through it i saw the same as before a table a search and a number in url title = 1 that can change so i did it this time in the search bar : 
  ![[Pasted image 20230330103949.png]]
  ```SQL
  1' union select 1,version(),3,database(),5,6,7-- #
```
- and it worked it gave me the info i needed :
	![[Pasted image 20230330104038.png]]
---
### SQL Injection (Sql Lite):
- Like before there is search bar so i tried to see all the columns by using : 
```SQL
' union select all 1,2,3,4,5,6,7-- #
```
- but returned an error so i decreased the values by 1 :
```SQL
' union select all 1,2,3,4,5,6-- # 
```
- it worked but there was something wrong  when i tried to get the database version:
```SQL
' union select all 1,2,3,database(),5,6-- #
```
- so  i searched for sqlite commands to get it's version and i found this
```SQLite
select sqlite_version()
```
- so i tried it in my select : 
``` SQL
' union select all 1,2,3,SQLite_version(),5,6-- # 
```
- and it worked ! 
![[Pasted image 20230330105019.png]]
---
## Sql blind - time - based:
- it was simple as it is about time so i tried this payload:
``` SQL
' 1=1 and sleep(1) #
```
- so it appeared that it took 1 second to reload that means that sql injection by time sleep is working on it.