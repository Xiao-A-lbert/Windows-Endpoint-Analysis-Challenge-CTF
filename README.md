# Windows Endpoint Analysis Challenge CTF

<h2>Description</h2>
In this Windows Endpoint Analysis Challenge, I used the commandline queries like netstat and tasklist to find the processid and associated DLL modules of the challenge.exe malware. I also used Autoruns and Task Scheduler to find persistences within the system. 

<h2>Languages and Utilities Used</h2>

- <b>Windows cmd</b>
- <b>Autoruns</b>
- <b>Task Scheduler</b>

<h2>Environments Used </h2>

- <b>Windows 10 Enterprise</b> 

<br />
<br />
Challenge promopt to execute the challenge.exe and infect my VM with persistence. 

![1) challenge prompt](https://github.com/user-attachments/assets/9b3d26a7-cff0-4d2a-bdb9-8f0ae00dcce0)

<br />
<br />
I used "netstat -anob" to show the port and processid the challenge.exe malware used.

![2) q2](https://github.com/user-attachments/assets/f2c6cb89-5018-43b7-9cbd-d0fa43d67539)

<br />
<br />  
I used "tasklist /FI "PID eq 2628" /M" to show the DLL modules used by the malware. 

![3) q4](https://github.com/user-attachments/assets/34c6afef-905e-4b9f-ba80-f3c88f91b021)

<br />
<br />
I used "wmic process where processid=2628 get name, parentprocessid, processid" to get the aprent processid for challenge.exe, then ran it again replaceing 2628 with 5236 to get the parent process of cmd.exe. 

![4) q5](https://github.com/user-attachments/assets/9179d559-81a5-489c-9154-fe5a2a308960)

<br />
<br />
I ran netshare to show the "xkalibur" share and its file path on the system. 

![5) q6   7](https://github.com/user-attachments/assets/aed909ef-fa1b-4396-94ab-02d5e6520fda)

<br />
<br />
Using Autoruns showed me the "CleanUpController" Run generated in HKEY_Current_User\..\Run and its file path. 

![7) q8910](https://github.com/user-attachments/assets/864c17cd-3448-42a7-995a-35b804a29323)

<br />
<br />
Using Autoruns show the "WindowsActiveService" persistence in HKEY_Local_Machine\..\Services and its file path. 

![8) q 11 12](https://github.com/user-attachments/assets/a14dc958-0f82-4ca7-ae2f-2558700f3dd4)

<br />
<br />
I ran "sc qc "windowsactiveservice" " to query the configuration of the persistene and found its start type. 


![9) q12](https://github.com/user-attachments/assets/f334a8f9-6890-42ac-87df-756ed87d98f2)

<br />
<br />
Still in Autoruns, I found "ayttpnzc"  scheduled task persistence and its file path. 

![10) q 14 15](https://github.com/user-attachments/assets/0ecee794-1948-4882-83d4-db7ad1228d8a)

<br />
<br />
Finding "ayttpnzc" in Task Scheduler showed its trigger time. 

![11) q16](https://github.com/user-attachments/assets/c24ac145-a609-4606-9e26-7cf39630db66)

<br />
<br />
That concludes the Windows Endpoint Analysis Challenge. I reverted my windows VM back to baseline pre challenge. 

![12) done](https://github.com/user-attachments/assets/82d03bb2-3596-4ac1-80d3-09cdea89370b)

<br />
<br />
