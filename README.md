# Analyzing Indicators of Compromise
Identifying and analyzing potential indicators of compromise using various digital forensic techniques.

**Wireshark pcap file analysis:**
    Open pcap file in Wireshark for analysis:

   ![image](https://github.com/user-attachments/assets/f5c72bfa-d7d7-43aa-9990-4243df413af6)

    
  Apply http filter to examine http traffic:

   ![image](https://github.com/user-attachments/assets/6add1b14-b8ad-4fe3-8448-23533d569aa4)

  There are some post requests with images, so check the TCP stream to find more information.

  ![image](https://github.com/user-attachments/assets/b9ea1b3d-2d01-40e4-afd5-54315b9462a6)
  
  The jpg images are not actual image files, but executable headers can be seen in the stream.
  Host is 2.56.57.108.

  As the data seem suspicious, get the details of the URI from the Hypertext Transfer Protocol section:

  ![image](https://github.com/user-attachments/assets/683d4cf7-bd4a-4a7a-adc9-0448cc82c04e)

  ![image](https://github.com/user-attachments/assets/85f6f1ce-1770-4a60-a669-6464c18b0a2e)

  URI: http://2.56.57.108/osk 

  Check if the URI is malicious in virus total website:

  ![image](https://github.com/user-attachments/assets/9e78829e-a8e2-45a2-9988-9cd134c2af52)

  The URI is malicious.

  Check if the host Ip address is malicious.

  ![image](https://github.com/user-attachments/assets/5bb5461f-7964-4bd0-87d8-eb0bd8420d12)

  The Host Ip address is malicious.

  Check if the URI is connected to any malicious malware in the threat fox IOC database.

  ![image](https://github.com/user-attachments/assets/d5ba789d-5aa2-44e0-99e1-27148f9bf82b)

  Oski Stealer malware can be associated with this malicious URI.

  Export HTTP objects list to further analyze:

  ![image](https://github.com/user-attachments/assets/d6c95725-9f8e-4471-81ce-11c7450240ec)

  Save the image files to further verify.
  Extract MD5 from image files using Hash my File utility.

  ![image](https://github.com/user-attachments/assets/f04d8fcd-25f9-493e-a11e-4a31db571bc7)

  Check MD5 hash value in virus total website to check if it is malicious.

  ![image](https://github.com/user-attachments/assets/210afb5d-24d1-4a30-b338-e2d86c61a01f)

  Confirmed gain that these files are malicious.

  TrID: Get the filetypes of these image files by running TrID in CMD on these files.

  ![image](https://github.com/user-attachments/assets/093e8de1-0aa7-4a74-9d99-616db71aa499)

  ![image](https://github.com/user-attachments/assets/33f92b1c-9b7f-46a3-b48a-8b831dcc26da)

  ![image](https://github.com/user-attachments/assets/b71513e0-af57-4ea8-a4db-8cf9f359d278)

  These image file contains .dll and .exe files.

  Check the TCP stream in Wireshark:

  ![image](https://github.com/user-attachments/assets/84d52b53-d6da-4930-b9e4-988d0e2c7b17)

  ![image](https://github.com/user-attachments/assets/38b8ea75-a648-45b2-85ec-3a45ddd68b77)

  Clearly there was an attack, and the malicious attacker had stolen sensitive data like browser cookies, autofill data from browsers, login credentials etc.

**Log analysis: **

  Check the entries in the log which got http status code 200 using awk.

  ![image](https://github.com/user-attachments/assets/8d243ff8-7477-475b-b6d6-0535349b8eb5)

 Check suspicious requests for any vulnerabilities:

 ![image](https://github.com/user-attachments/assets/51fa69ba-ed68-4e33-b5c4-66b74f75305b)

 () { :; }; string is seen in the user agent header, which means the attacker exploited the shell shock vulnerability. This is the same Ip address that is involved in the malicious attack found from Wireshark. 

 Checking URI found in the user agent field, to confirm if its malicious.

 ![image](https://github.com/user-attachments/assets/ff28f442-ae54-4b72-a852-a57667689286)

 ![image](https://github.com/user-attachments/assets/385c831d-39f7-49c0-8034-60ae0f0ff125)

 It was tagged as malicious in the virus total website.

Some more malicious Ip addresses were found which received as 200 status code from the server. Below are the details from the virus total website.

![image](https://github.com/user-attachments/assets/0a50b52f-5b91-45cf-bd32-1bcbecb1ff0f)

![image](https://github.com/user-attachments/assets/521908f2-c99f-43cc-a640-b508f9bf9f6b)

![image](https://github.com/user-attachments/assets/00319152-41a7-44c1-ad4d-dba6371ccefb)

![image](https://github.com/user-attachments/assets/08a56a0d-0b06-4ecf-aeeb-dab443627974)

**Reporting: **
Used Serpico tool to save the artifacts and generate a digital forensic report.

![image](https://github.com/user-attachments/assets/41ac7f83-b229-4477-97f7-080cfcb334b5)

![image](https://github.com/user-attachments/assets/603234ba-7dac-4677-9b81-49da0d669d08)

Upload the IOCs, artifacts, and evidence.

![image](https://github.com/user-attachments/assets/cdfba718-a6aa-4033-890b-0bc7a3cd853e)

![image](https://github.com/user-attachments/assets/e4ea171e-aaa6-4ba7-be57-6b233e3298ed)

Generate the forensic report:

![image](https://github.com/user-attachments/assets/49ac312e-d062-4af1-a9cc-abbc0446bb2f)

![image](https://github.com/user-attachments/assets/b64f0d77-3316-4b98-9fc4-a4c3859355e7)

**Conclusion:** Several potential Indicators of compromise (IOCs) were identified in the data, allowing suspicious network traffic from malicious Ip addresses, presence of malware, and unauthorized access to sensitive data.Digital forensic techniques such as Log analysis, Network packet traffic analysis, Reverse steganography and Malware analysis were used to 
  conduct the investigation.


 
















  












