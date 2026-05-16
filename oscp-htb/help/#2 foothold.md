the exploit 41200.py won't work, so we'll have to recreate the sqli manually
![[scrns/Pasted image 20260505110323.png]]

login with the found credentials and submit a ticket
![[scrns/Pasted image 20260506133805.png]]

copy the url link of the ticket and intercept it with burp
![[scrns/Pasted image 20260506133844.png]]

save the request and test it with sqlmap
![[scrns/Pasted image 20260506134029.png]]

it reveals that the get request is vulnerable
![[scrns/Pasted image 20260506134100.png]]

sqlmap can dump the whole database, but we'll do it manually

adding a basic payload like " and 1=1 -- -" (true) in URL encoded form returns the jpeg attached, while "1=2" (false) returns 200 response but "Page not found - 404" in the body.
![[scrns/Pasted image 20260506135141.png]]

![[scrns/Pasted image 20260506135240.png]]

in the helpdeskz github there is the following that reveals a possible sql table for users/passwords
![[scrns/Pasted image 20260506135312.png]]

revealing also the password hash format
![[scrns/Pasted image 20260506135855.png]]

using the " and substr((select password from staff limit 0,1 ),1,1) = '' we can extract the password one letter at the time.
![[scrns/Pasted image 20260506140014.png]]

the method is very slow so we'll use the following script
[[../../blind sqli brute script/blind sqli brute script]]

![[scrns/Pasted image 20260506140222.png]]

![[scrns/Pasted image 20260506140241.png]]

do the same for retrieving the email with the alt options in script
![[scrns/Pasted image 20260506141630.png]]

ssh must be guessed, login as help and get user flag
![[scrns/Pasted image 20260506142212.png]]
