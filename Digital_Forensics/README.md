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


