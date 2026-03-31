# Benign TryHackMe Walkthrough
Write-up from the TryHackMe Room Benign where I used splunk to investigate a compromised host.

Room URL: https://tryhackme.com/room/benign

My Profile: https://tryhackme.com/p/xavicdiez

---

### How many logs are ingested from the month of March, 2022?
Answer: 13959

<img width="939" height="506" alt="image" src="https://github.com/user-attachments/assets/92bd8c27-98bc-4606-a812-2f04336a2b3f" />

### Imposter Alert: There seems to be an imposter account observed in the logs, what is the name of that user?
Answer: Amel1a

Doing this search we found that there is a rare value in the UserName category.
<img width="939" height="94" alt="image" src="https://github.com/user-attachments/assets/05103e05-40c7-43a5-b277-d71bd2e92643" />
<img width="939" height="97" alt="image" src="https://github.com/user-attachments/assets/26ed983c-d83b-4d86-a54a-3e3116fd309a" />

### Which user from the HR department was observed to be running scheduled tasks?
Answer: Chris.fort

For this question I crafted the next query:

<img width="939" height="61" alt="image" src="https://github.com/user-attachments/assets/59c92175-ab08-4713-b632-c5419ac6e84e" />

I am searching for the exact process schtask.exe which is the Schedule Task process and the command line containing /create which is used to create task.

<img width="939" height="469" alt="image" src="https://github.com/user-attachments/assets/689deedb-e408-4fd0-8045-0d0396262e58" />

### Which user from the HR department executed a system process (LOLBIN) to download a payload from a file-sharing host.
Answer: haroon

In this question we are told that a user of the HR department downloaded a payload, so the query crafted contains all the HR UserNames and the command line containing https since we know that the user downloaded the payload from a file-sharing host.
<img width="939" height="89" alt="image" src="https://github.com/user-attachments/assets/b9541cd6-3ac9-4cb6-9f13-b18a0dfe7fe9" />
<img width="939" height="378" alt="image" src="https://github.com/user-attachments/assets/62aea4ee-0348-46fb-ad6f-4a121f79e2bb" />

```
The questions 5, 6, 7, 8, 9 and 10 were answered by looking the previous images.
```

### To bypass the security controls, which system process (lolbin) was used to download a payload from the internet?
Answer: certutil.exe

### What was the date that this binary was executed by the infected host? format (YYYY-MM-DD)
Answer: 2022-03-04

### Which third-party site was accessed to download the malicious payload?
Answer: controlc.com

### What is the name of the file that was saved on the host machine from the C2 server during the post-exploitation phase?
Answer: benign.exe

### The suspicious file downloaded from the C2 server contained malicious content with the pattern THM{..........}; what is that pattern?
Answer: THM{KJ&*H^B0}

By visiting the URL from the image, we can obtain the answer.

# What is the URL that the infected host connected to?
Answer: hxxps[://]controlc[.]com/e4d11035
The URL is defanged.


