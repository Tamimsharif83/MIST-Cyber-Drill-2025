![image](https://github.com/user-attachments/assets/c20a6f07-7287-4306-84ba-f3bf7c3122b9)

This was the first question of the forensics section. There is a link to a file named cat.gz, which is a zip file. Upon unzipping, a file named **cat** is obtained. While checking the file type, it is identified to be in **MBR** format, which primarily indicates a **disk image**.
![image](https://github.com/user-attachments/assets/485d25fb-0019-458a-be6c-41fa6e196152)

In the first question, the **MD5 hash value** of the **cat image file** is requested. I used my **Linux command shell** to find it, and I successfully obtained the hash value.

![image](https://github.com/user-attachments/assets/e3943f05-5873-43c1-8280-572e8634ef94)

**flag:WTISD{19f436d1d00b384af7e9d882f045ff92}**


![image](https://github.com/user-attachments/assets/770bdd62-2c48-4e5d-bf36-ef41e0990a89)


Here, the **partition format of the disk image file** is requested. Although this can be determined using the **command shell**, I chose to open and analyze the disk image using **Autopsy**, where the partition format can be directly viewed.


![image](https://github.com/user-attachments/assets/87ca0f72-4bbe-4067-9a1e-1e902d4953a5)


I opened **Autopsy using Kali Linux**. After creating a **new case**, providing a **host name**, and specifying the target file directory, I was able to view the **partition format** of the image file. The partition format of this image file was **FAT32**.


![image](https://github.com/user-attachments/assets/564fdc71-d3a2-4113-b68c-b7a6bd700ec9)


**flag:WTISD{FAT#@}**

![image](https://github.com/user-attachments/assets/c1650203-70ad-4dd1-948d-2104a3ff7969)


Sure! Here’s your paragraph in a smooth, clear English format:

This task was quite straightforward. When I used the **file command**, it displayed all the sector information clearly, including the start sector at 2048, the total number of sectors as 260,096, and that it was an extended partition table (last). This made understanding the partition layout much easier.

![image](https://github.com/user-attachments/assets/485d25fb-0019-458a-be6c-41fa6e196152)

**flag:WTISD{2048, 260096}**

![image](https://github.com/user-attachments/assets/cc6773e5-8ffb-463f-a006-707d23c76bdc)


When I started the analysis using Autopsy’s file analysis option, I found a directory named **Documentation**

![image](https://github.com/user-attachments/assets/a2fa976a-1696-49c8-b452-945da30d57fe)


![image](https://github.com/user-attachments/assets/895df52d-072e-4374-add2-e8492c540b2d)

. Inside that directory, I discovered a file called **La résistance électronique.pdf**, which was marked in red, indicating it was a **deleted file**. Along with the file, I also obtained various other information, including its size (672,623 bytes).

**flag: WTISD{672,623 bytes}**


![image](https://github.com/user-attachments/assets/a8c8c054-bf7e-4293-8b56-5f3b3241cb43)

![image](https://github.com/user-attachments/assets/cde6e0a4-05d5-441e-8b2b-54881a19e61b)
I navigated to the **Documentation directory** and found several PDF files. This made me suspect that there could be a **telephone number** among them. With this in mind, I downloaded a file named **tartes\_flambee\_a\_volonte\_francais\_2013.pdf**, but it was saved as **Autopsy**. When I checked the file type using the **file command**, it showed as a **data file**.

![image](https://github.com/user-attachments/assets/df554f12-5681-4fe6-9e77-63e505ca9b55)


However, since it was initially a PDF, I used the **pdftotext command** to extract the text content,


![image](https://github.com/user-attachments/assets/5d64e51d-b9ed-4fe2-81c9-6a60ee15a478)


which was saved as **Autopsy.txt**. Upon reviewing the text, I noticed a pattern like **Tel: xxx xxx xxx**, which is typically a telephone number format. My assumption was further confirmed when I saw the phrase **"Au cœur de la Petite France"** within the text file.

![image](https://github.com/user-attachments/assets/45c247b0-2251-4e56-87f6-48aa3fb5a72e)

**flag: WTISD{0033388324513}**


![image](https://github.com/user-attachments/assets/d246f0f8-137e-4a92-b8bf-defb647140be)


In Autopsy, under the **Documentation directory**, there is a PDF file named **"Courba13-01.pdf"**. I displayed it in **ASCII string format**, 



![image](https://github.com/user-attachments/assets/abf4c79e-3531-4344-ab42-95312bbff770)


and after scrolling down, I could view the **PDF file's metadata**. Among the metadata, I found the **author/creator's name**, which was **Olivier**.


![image](https://github.com/user-attachments/assets/79cd456d-a781-4be0-861d-cb8253f24c6f)

**flag: WTISSD{Olivier}**

![image](https://github.com/user-attachments/assets/910acfb5-75ab-4e29-9ec1-16d0cb273ef4)

This question was quite easy for me, but due to the pressure of the contest, I completely forgot the simple solution. Instead, I spent over an hour manually searching for the hash in **Autopsy**, and although I found other hash files, I couldn’t locate the one I needed.

![image](https://github.com/user-attachments/assets/613edc92-cd6c-4b93-b1d7-e484768f9372)


Suddenly, I remembered that I regularly use **VirusTotal**, a tool that can identify a file name using its hash value. Within just a minute, the problem was solved.

![image](https://github.com/user-attachments/assets/2ae8cad1-542e-4e0a-bc8f-16d00d03ba69)



![image](https://github.com/user-attachments/assets/ecf1bda5-1adc-4f28-ae67-f39edf077a68)


**flag:WTISD{magnify-clip.png}**


![image](https://github.com/user-attachments/assets/6d2ce358-5b80-477d-b3be-80a1ea78f448)



I initially thought I needed an image to find this information. So, I navigated to the path **/WebSites/ /L'autonomie de l'Alsace\_files/**, where I found several images, including **51489545tag-elsass-frei-jpg.jpg**. After viewing this image, I used **Google Image Search** (Google Scanner) and quickly identified the **place name**.

![image](https://github.com/user-attachments/assets/f9230e8b-649f-4783-ae47-fc88e24ca74e)


**flag: WTISD{WTISD{Alsace}}**

![image](https://github.com/user-attachments/assets/608a7bcf-4473-4dba-9a96-4ec3e9a500f8)

After navigating to **C:/ /Files/**, I found a **deleted ODT file**. While viewing it in **ASCII string format**, I noticed the term **jpg**, which made me suspect that there might be some hidden information. So, I exported the ODT file, where I discovered a **cat image and a note**. The note, when translated to English, read: **"GIVE AUTONOMY BACK TO ALSACE OR WE WILL KILL THE CAT!!!"** Oh no, it was a threat!

I immediately downloaded the **cat image** and began a **metadata analysis** using **ExifTool**. During this analysis, I found the **GPS Latitude and Longitude** of the location where the image was taken. After searching these coordinates on **Google Maps**, I identified a place. Upon zooming in, I saw a **town hall**, which became a crucial flag in this investigation.


![image](https://github.com/user-attachments/assets/b5300a31-2644-4efd-883f-8d7ae026f5eb)


