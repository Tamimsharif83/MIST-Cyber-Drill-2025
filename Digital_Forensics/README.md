Forensic 1

Your game starts here.

A password-protected ZIP file awaits you.

The key to unlock it is the File Signature.  

Think fast, act faster — time is ticking.

Unlock the ZIP file to begin your mission.

Find out the sender email address. link (email.7z)

ANSWER:

First, this file was password-protected with 7-Zip. It took a long time to crack the password because, at the start of the contest, the file signature was missing. I was trying to crack it using a dictionary attack, but the password didn't match.

I cloned this GitHub repository: https://github.com/Goron/7zip-crack and used it to perform a dictionary attack.


![image](https://github.com/user-attachments/assets/5fe17391-0d00-47cf-ad62-2caf4aa21f4e)

I was feeling really bad at one point and thought I wouldn't be able to solve the forensics challenge because all 10 forensics questions were based on this file. But when they updated the questions and I saw that FILE SIGNATURE was given as a hint, I felt hopeful to start again.

Still, even after trying many formats of the .7z file signature's magic value, I couldn't crack it. I even tried using the magic numbers of .txt and .eml files, but just like before, it left me frustrated.

Two hours after the contest started, I finally succeeded. I tried using the .7zip magic value format from this Wikipedia https://en.wikipedia.org/wiki/List_of_file_signatures as the password, and it worked.
![image](https://github.com/user-attachments/assets/fb6bb9be-a23b-4c66-b4e8-454cc4f0e162)

After extracting the 7-Zip file, I found a file named **email.txt** and started analyzing it as per the questions.

The first question was quite easy: **"Find out the sender's email address?"**

**Look for the "From" Field:**

In the email header, the "From" field shows the sender's name and email address.

The sender's email address in the provided email header is: **[bob@linode.com](mailto:bob@linode.com)**.
![image](https://github.com/user-attachments/assets/fc47d284-57d3-45a0-b0c3-de051ed76a51)

WTISD{bob@linode.com}


Forensic 2

From the sender email address find out the domain registrar and domain creation date? (example: registrar, dd.mm.yyyy)



Specific format for this flag is: WTISD{XXXXXXXXXX, Inc., DD.MM.YYYY}

ANSWER:

This was a common question for me. I searched for the sender's email domain using **ICANN Lookup**, where I found all the necessary details.
![image](https://github.com/user-attachments/assets/32d17b5d-21e3-43ab-9600-3c3dd5849747)

![image](https://github.com/user-attachments/assets/bdce4bf4-0cf6-4e1e-903f-491eee8132c7)

![image](https://github.com/user-attachments/assets/6a6f26fc-27c6-4260-88fd-fbee46a303c0)

Flag is: WTISD{Markmonitor, Inc., 26.01.2003}

Forensic 3

What is the IP Address of the originating e-mail server 

Flag format for this challenge is WTISD{flag}

ANSWER:

The Originating Email Server is the first server from which the email was sent, meaning the point where the email first entered the internet.

Key Points for Analysis:

The email header usually has multiple "Received" fields, each showing the servers the email passed through.

The bottom "Received" field (or the first one) is the initial server.

If this server shows a private IP (10.x.x.x, 192.168.x.x), we look for the next public IP in the next "Received" field.

In This Case:

I carefully checked the "Received" fields.

The second "Received" field contained the public IP address (139.144.239.74).

So, this is the IP of the originating email server.

Final Answer:

Flag: WTISD{139.144.239.74}

Forensic 4
From the above IP find out the ISP’s location? (example: city, region) link

Flag format for this challenge is WTISD{flag}

ANSWER:

To see the ISP, location, and other details of the IP address (139.144.239.74), I went to an IP lookup website and searched for this IP https://www.iplocation.net/ip-lookup. 
![image](https://github.com/user-attachments/assets/f2887b73-1f64-4f59-baa9-ae1f235e86c8)


I quickly found all the information I needed. It was actually quite simple.

WTISD{Cedar Knolls, New Jersey}

Forensic 6

What is the domain name of the receiving server 

Flag format for this challenge is WTISD{flag}

ANSWER:

It was very easy because the answer was directly given in the file.

![image](https://github.com/user-attachments/assets/175c1352-f091-4a80-ae9f-15b7070b43a8)

WTISD{mx.google.com}


Forensic 7

From the received header find out the reported time zone (example: Greenwich Mean Time) 
Flag format for this challenge is WTISD{flag}

ANSWER:

The time here is 09:29:19 -0500, which is Eastern Standard Time (EST).

![image](https://github.com/user-attachments/assets/5e60d7f4-530a-4f59-8aa0-bda91e26f1c6)

WTISD{Eastern Standard Time}

Forensic 8:

What is the time zone of the final receiving e-mail server (example: Greenwich Mean Time) link

Flag format for this challenge is WTISD{flag}

ANSWER:

The final receiving server is the one that directly delivered the email to the recipient (Gmail in this case).
This is identified by the topmost "Received" field in the header.

![image](https://github.com/user-attachments/assets/df5ac268-8eff-45a5-92d3-fd11153f5bb7)

PST (Pacific Standard Time) is equivalent to UTC -8 hours.
WTISD{Pacific Standard Time}

Forensic 9

What is the file name specified in the link of the body of the e-mail? (example: name.extension) 
Flag format for this challenge is WTISD{flag}

ANSWER:

Towards the end of the text file, I noticed a filename that looked like a flag.
![image](https://github.com/user-attachments/assets/d4f81072-d5a9-437f-9a96-f6f1d32f3ffa)

I submitted it, and it was accepted. Yeah!!
WTISD{Your_account_is_compromised.exe}

Forensic 10
What is written on the floating balloon 
Flag format for this challenge is WTISD{random string}

ANSWER:

Seeing the word "beloon" in the question, I thought there might be a picture. Soon, I noticed a line in the file:

Content-Type: image/jpeg; name="Have a good day.jpg"
![image](https://github.com/user-attachments/assets/c2035b27-e3da-4114-85a7-411557747ed4)

But I wondered, "Where is the picture?"That's when I noticed a block of Base64 encoded data.
![image](https://github.com/user-attachments/assets/cc21cf69-7f48-4d17-93dd-6825cfc5c111)

I immediately realized that I could convert this Base64 data into an image.
I immediately searched "Base64 to image" on Google and used this link: https://base64.guru/converter/decode/image.

I pasted my Base64 data there, and w0w, so niceeee! 🎉
![image](https://github.com/user-attachments/assets/fad169fe-2f47-4d7b-9314-934123dc2bfb)

I finally got my expected balloon image, and the text on the balloon was: "Get Well Soon."
	WTISD{Get Well Soon}

Conclusion

After successfully cracking the 7-Zip password and analyzing the email.txt file, I tackled all the forensics questions step by step. I used various techniques like WHOIS lookups, IP address analysis, and Base64 decoding to extract the required information. The entire challenge was both fun and rewarding, and I was able to find all the flags and complete the task with success!
