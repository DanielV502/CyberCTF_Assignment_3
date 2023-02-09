# CyberCTF_Assignment_2

### 1. Challenge: file-run1 (Easy)

* The challenge request to download and run a program.

		#!/bin/bash
		#Select the commands needed to Get the Flag!

		#Download the program to run on terminal
		wget "https://artifacts.picoctf.net/c/308/run"
		echo ""
		#Set the file as an executable
		chmod +x run

		#Run the downloaded program
		./run
		echo ""

* The script provide some comments to guide through the capture of the flag, the download of the program and the output is the flag:
 

> The flag is: “picoCTF{U51N6_Y0Ur_F1r57_F113_9bc52b6b}”

### 2. Challenge: file-run2 (Easy)

* The challenge request to download and run a program with an argument.
  
		#!/bin/bash
		#Select the commands needed to Get the Flag!

		#Download the program to run on terminal
		wget "https://artifacts.picoctf.net/c/351/run"
		echo ""
		#Set the file as an executable
		chmod +x run

		#Run the downloaded program with an argument
		./run Hello!
		echo ""

*	The script provide some comments to guide through the capture of the flag, the download of the program and the output is the flag:
 

> The flag is: “picoCTF{F1r57_4rgum3n7_be0714da}”




### 3. Challenge: CVE-XXXX-XXXX (Easy)

* The challenge asks to look for the (RCE) vulnerability in 2021 in the Windows Print Spooler Service.
*	The Summary of the vulnerability is that an attacker who successfully exploited this vulnerability could run arbitrary code with SYSTEM privileges.
o	Source: https://msrc.microsoft.com/update-guide/vulnerability/CVE-2021-34527

> The flag is: “picoCTF{CVE-2021-34527}”





### 4. Challenge: Local Authority (Medium)

* The challenge asks to look for a website with a login prompt.
    

* There was some information on the validation of credentials where the user and password was stored allowing us to login the website:

> The flag is: “picoCTF{j5_15_7r4n5p4r3n7_05df90c8}”

* 5. Challenge: Power Cookie (Medium)

* The challenge asks to look for a website with a button to login as guest.
   
 

* On the inspection of the website files, there was a cookie with a parameter to login as a Guest, modifying this cookie allow us to login as admin:

> The flag is: “picoCTF{gr4d3_A_c00k13_5d2505be}”










### 6. Challenge: Forbidden Paths (Medium)

*	The challenge asks to get the flag from a website with absolute file path filtering from the files structure.


* The file path provided is: “usr/share/nginx/html/flag.txt”
* The absoulte file path is filtered, with a relative file path we can get the flag:“../../../../flag.txt”

 

> The flag is: “picoCTF{7h3_p47h_70_5ucc355_6db46514}”
