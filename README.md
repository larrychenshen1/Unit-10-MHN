**Unit-10-MHN**

Objective: We're under attack, so we should do counter-survelliance to see who's attacking us. 

**MHN-Admin Deployment in GCP**

![Image 11-18-22 at 2 40 PM](https://user-images.githubusercontent.com/112603335/202815045-97f0b548-898e-4c1b-86c4-0caba596ba99.jpg)

**Dionaea Honeypot Deployment**

a malware catching honeypot, like the venus fly trap

**Database Backup**

MHN-Admin stores data captured in MongoDB, a NoSQL database. <br>
CRUD operations apply to traditional relational database management systems (such as PostgreSQL or SQL Server) and the more recent NoSQL databases MongoDB or DynamoDB

**Export honeypot data**

Detailed logs can be exported from honeypot to parse. Data sets include source IP, protocol, timestamp, etc. <br>
Sample log entry below: 
```
{"_id":{"$oid":"636984e5616a1e65521c59b5"},"protocol":"Blackhole","hpfeed_id":{"$oid":"636984e4616a1e65521c59b4"},"timestamp":{"$date":"2022-11-07T22:21:24.626Z"},"source_ip":"45.64.179.222","source_port":44663,"destination_port":23,"identifier":"70339b6a-5eea-11ed-b24b-42010a8a0002","honeypot":"dionaea"}
```
**Deploying Additional Honeypot(s)**

Ubuntu - wordpot: Wordpress honeypot that attracts/detects probes for possible Wordpress vulns (plugins/installation/themes/etc.)

**Malware Capture and Identification**

Trojan.Win32.Wanna.epxkni <br>
- detected by MHN Dionaea honeypot <br>
- WannaCry ransonware uses the infamous NSA EternalBlue zero day crack in Windows Server Message Block (SMB) on Windows 7 SP1 hosts. NSA first detected this vuln but did not annouce to Microsoft to patch and eventually was this vuln was leaked when NSA was cracked themselves by the Shadow Brokers. <br>
- MD5 Hash: d25171479677bde36fba4f25c44bd851 <br>
- SHA512 Hash: 68e99dcbbc22703ff2c2f11c1dd9fece52ac2283e9dadc94c1afeab2af9bf96a4a5f1203afbaea090b67d020a08e7d88b30a3b475194fbf173d4f3f582256797

**Challenges with this Assignment**

Creating new MHN Honeypot VMs in GCP is 'pythonic' in the sense that white space matters. <br>
When trying to copy/paste the multi-line command directly into GCP's Cloudshell, I couldn't create a new honeypot *unless* the spacing met syntax rules exactly. I believe I lost precise spacing syntax when using various copy/paste commands on macOS notepads like bbedit, Apple Notes, etc. 

```
gcloud compute instances create "honeypot-2” \
    --machine-type "n1-standard-1" \
    --subnet "default" \
    --maintenance-policy "MIGRATE" \
    ...
```
**Time spent: 7 hours spent in total**
