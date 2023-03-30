## Reflected-Post
- First i tried to give a normal first name and last name and it returned them as a welcome answer 
- So i started to think what will happen if i gave it <" in the first name and any thing in the second name i found out that it accepts it normally
- I tried to give it a pay load:
```HTML
<script>alert(1)</script>
```
- and it worked it returned the alert.
---
### XSS -Reflected(HREF):
- so i tried by typing any thing and it gave ma whole table of things to vote
- looked at the view source window and i found that there is an href that doesn't end with > 
- so i typed as follows:
```html
><script>alert(1)</script>
```
- and it worked!

---
## XSS - Stored ( Cookies):
- so when i tried to see it there was nothing i can write at so i thought of using burp suite to intercept it
- so when i intercepted it i found out the cookies so i can change it to what ever i want.
---
## XSS - SqliteManager :
- So  when i opened the website it told me that the version 1.4.2 is vulnurable
- so i got to the sqllite manager and got to test
- gave it a trigger with my name and the script
```html
<script>alert(1)</script>
```
- so the alert worked!
