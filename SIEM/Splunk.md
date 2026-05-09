## SPLUNK

### 1)Modify and employ the Splunk search provided at the end of this section on all ingested data (All time) to find all process names that made LDAP queries where the filter includes the string *(samAccountType=805306368)*. Enter the missing process name from the following list as your answer. N/A, Rubeus, SharpHound, mmc, powershell, _

I'm just modifed query to hack the box 
index=main source="WinEventLog:SilkService-Log"
| spath input=Message 
| rename XmlEventData.* as * 
| table _time, ComputerName, ProcessName, ProcessId, DistinguishedName, SearchFilter
| sort 0 _time
| search SearchFilter="*(samAccountType=805306368)*"
| convert ctime(maxTime)

And i'm find rundll32

### 2)Employ the Splunk search provided at the end of this section on all ingested data (All time) and enter the targeted user on SQLSERVER.corp.local as your answer.

Im utilised 
index=main  source="WinEventLog:Security" EventCode=4625 dest="SQLSERVER.corp.local"
| bin span=15m _time
| stats values(user) as Users, dc(user) as dc_user by src, Source_Network_Address, dest, EventCode, Failure_Reason
And i'm find sa

### 3)Modify and employ the provided Sysmon Event 22-based Splunk search on all ingested data (All time) to identify all share names whose location was spoofed by 10.10.0.221. Enter the missing share name from the following list as your answer. myshare, myfileshar3, _


index=main   10.10.0.221 EventCode=22
| table _time, EventCode, source, name, user, Target_Server_Name, Message, IpAddress, Source_Network_Address, Target_Server_Name, QueryName
| sort 0 _timeyy

I'm find  f1nancefileshare
 ### 4)Modify and employ the Splunk search provided at the "Detecting Kerberoasting - SPN Querying" part of this section on all ingested data (All time). Enter the name of the user who initiated the process that executed an LDAP query containing the "*(&(samAccountType=805306368)(servicePrincipalName=*)*" string at 2023-07-26 16:42:44 as your answer. Answer format: CORP\_
First 
index=main source="WinEventLog:SilkService-Log"
| spath input=Message 
| rename XmlEventData.* as * 
| table _time, SubjectUserName, User, ProcessName, SearchFilter, _raw, XmlEventData,XmlEventData.PName
| search SearchFilter="*(&(samAccountType=805306368)(servicePrincipalName=*)*"

Second
index=main ProcessId=7136 OR PID=7136
| table _time, ComputerName, ProcessName, SubjectUserName, User, _raw

### 5)A Pass-the-Hash attack took place during the following timeframe earliest=1690543380 latest=1690545180. Enter the involved ComputerName as your answer.
index=main earliest=1690543380 latest=1690545180 (source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=10 TargetImage="C:\\Windows\\system32\\lsass.exe" SourceImage!="C:\\ProgramData\\Microsoft\\Windows Defender\\platform\\*\\MsMpEng.exe") OR (source="WinEventLog:Security" EventCode=4624 Logon_Type=9 Logon_Process=seclogo)
| sort _time, RecordNumber
| transaction host maxspan=1m endswith=(EventCode=4624) startswith=(EventCode=10)
| stats count by _time, Computer, SourceImage, SourceProcessId, Network_Account_Domain, Network_Account_Name, Logon_Type, Logon_Process
| fields - count

### 6)Execute the Splunk search provided at the end of this section to find all usernames that may be have executed a Pass-the-Ticket attack. Enter the missing username from the following list as your answer. Administrator, _

index=main earliest=1690392405 latest=1690451745 source="WinEventLog:Security" user!=*$ EventCode IN (4768,4769,4770) 
| rex field=user "(?<username>[^@]+)"
| rex field=src_ip "(\:\:ffff\:)?(?<src_ip_4>[0-9\.]+)"
| transaction username, src_ip_4 maxspan=10h keepevicted=true startswith=(EventCode=4768)
| where closed_txn=0
| search NOT user="*$@*"
| table _time, ComputerName, username, src_ip_4, service_name, category

### 7)Employ the Splunk search provided at the end of this section on all ingested data (All time) to find all involved images (Image field). Enter the missing image name from the following list as your answer. Rubeus.exe, _.exe

index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" (EventCode=3 dest_port=88 Image!=*lsass.exe) OR EventCode=1
| eventstats values(process) as process by process_id
| where EventCode=3
| stats count by _time, Computer, dest_ip, dest_port, Image, process


### 8)For which "service" did the user named Barbi generate a silver ticket?

index=main (EventCode=4769 OR EventCode=4648 OR EventCode=4624)
Account_Name="Barbi"
| eval Service=coalesce(Service_Name, Target_Server_Name)
| table _time EventCode ComputerName Account_Name Account_Whose_Credentials_Were_Used Service Client_Address Message
| sort _time

I's cif

### 9)Construct a Splunk query targeting the "ssh_bruteforce" index and the "bro:ssh:json" sourcetype. The resulting output should display the time bucket, source IP, destination IP, client, and server, together with the cumulative count of authentication attempts where the total number of attempts surpasses 30 within a 5-minute time window. Enter the IP of the client that performed the SSH brute attack as your answer.

index="rdp_bruteforce" sourcetype="bro:rdp:json"
| bin _time span=5m
| stats count values(cookie) by _time, id.orig_h, id.resp_h
| where count>30

### 10)Use the "cobaltstrike_beacon" index and the "bro:http:json" sourcetype. What is the most straightforward Splunk command to pinpoint beaconing from the 10.0.10.20 source to the 192.168.151.181 destination? Answer format: One word

timechart

### 11)Use the "kerberos_bruteforce" index and the "bro:kerberos:json" sourcetype. Was the "accrescent/windomain.local" account part of the Kerberos user enumeration attack? Answer format: Yes, No

index="kerberos_bruteforce" sourcetype="bro:kerberos:json" client="accrescent/windomain.local"
| search error_msg!=KDC_ERR_PREAUTH_REQUIRED

