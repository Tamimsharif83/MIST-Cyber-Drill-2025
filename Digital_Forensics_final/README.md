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
