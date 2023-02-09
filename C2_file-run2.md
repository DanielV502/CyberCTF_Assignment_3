# CyberCTF_Assignment_2

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

![R3_C2_1](https://user-images.githubusercontent.com/124681007/217722927-5ee457d6-8cd2-4e04-9044-99cc8d04154b.png)

> The flag is: “picoCTF{F1r57_4rgum3n7_be0714da}”
