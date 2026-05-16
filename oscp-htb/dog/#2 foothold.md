github search for backdrop cms reveals enumeration script 
![[scrns/Pasted image 20260502060923.png]]

the script contains a new directory for enumerating users
![[scrns/Pasted image 20260502061038.png]]

ffuf reveals possible users
![[scrns/Pasted image 20260502061121.png]]

format the username file
![[scrns/Pasted image 20260502061159.png]]

password spray (tiffany:BackDropJ2024DS2024 logs in)
![[scrns/Pasted image 20260502061233.png]]

create the shell directory and replace the shell.php with pentestmonkey rev shell
![[scrns/Pasted image 20260503112010.png]]

tar and upload/install
![[scrns/Pasted image 20260503112152.png]]

setup listener and visit address to execute.

user johncusack has the same "database" password
![[scrns/Pasted image 20260503112349.png]]

get user flag.

