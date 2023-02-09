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
