# CyberCTF_Assignment_3

### 7. Challenge: WordPress Website (Hard)

* The challenge requests to find the user names and passwords of the provided Website.
* With the tool “WPSscan” we scan the Website and get the associated users:
	* “admin”
	* “think”

![R3_C7_1](https://user-images.githubusercontent.com/124681007/217726362-db19feda-8185-4aa2-9722-955912b9c9d7.png)

![R3_C7_2](https://user-images.githubusercontent.com/124681007/217726419-6c06d2bb-1ee9-4552-ae97-867e1be98468.png)

* We can get the password hard-coded of the user “think” from the Webite files “123”.
* Now we have a way to get into the Website and in combination with the password list provided, we can automate the password search:

![R3_C7_3](https://user-images.githubusercontent.com/124681007/217726968-cf53b41a-718a-440d-9f8c-e0280a20af3a.png)

* The script has loop with a curl instruction to log on the Website, the localhost IP: **172.17.100.1**
* To void the security of the Website, we make a cycle with a successful login and another attempt with the password list until it gets a match.

> The password of the **“admin”** user is: **“#1mama”**













