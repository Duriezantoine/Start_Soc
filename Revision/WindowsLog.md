## WINDOWS LOG

### Page 1
#### 1)Analyser l'événement avec ID 4624, qui a eu lieu le 3/3/2022 à 10:23:25. Menez une enquête similaire comme indiqué dans cette section et indiquez le nom de l'exécutable responsable de la modification des paramètres de vérification comme réponse. Format de réponse: T_W_____.exe
TiWorker.exe
#### 2)Build an XML query to determine if the previously mentioned executable modified the auditing settings of C:\Windows\Microsoft.NET\Framework64\v4.0.30319\WPF\wpfgfx_v0400.dll. Enter the time of the identified event in the format HH:MM:SS as your answer.
10:23:50

### Page 2
#### 1)Répliquez l'attaque de détournement DLL décrite dans cette section et fournissez le hachage SHA256 du WININET.dll malveillant comme réponse. "C:\Tools\Sysmon" et "C:\Tools\Reflettive DLLInjection" sur la cible engendrée contiennent tout ce dont vous avez besoin.
51F2305DCF385056C68F7CCF5B1B3B9304865CEF1257947D4AD6EF5FAD2E3B13
#### 2)Répliquez l'attaque PowerShell non gérée décrite dans cette section et fournissez le hachage SHA256 de clrjit.dll que spoolsv.exe chargera comme votre réponse. "C:\Tools\Sysmon" et "C:\Tools\PSInject" sur la cible engendrée contiennent tout ce dont vous avez besoin.
8A3CD3CF2249E9971806B15C75A892E6A44CCA5FF5EA5CA89FDA951CD2C09AA9
#### 3)Répliquez l'attaque de dumping d'informations d'identification décrite dans cette section et fournissez le hachage NTLM de l'utilisateur administrateur comme réponse. "C:\Tools\Sysmon" et "C:\Tools\Mimikatz" sur la cible engendrée contiennent tout ce dont vous avez besoin.
5e4ffd54b3849aa720ed39f50185e533

### Page 4
#### 1)Replicate executing Seatbelt and SilkETW as described in this section and provide the ManagedInteropMethodName that starts with "G" and ends with "ion" as your answer. "c:\Tools\SilkETW_SilkService_v8\v8" and "C:\Tools\GhostPack Compiled Binaries" on the spawned target contain everything you need.
GetTokenInformation

### Page 5
#### 1)Utilize the Get-WinEvent cmdlet to traverse all event logs located within the "C:\Tools\chainsaw\EVTX-ATTACK-SAMPLES\Lateral Movement" directory and determine when the \\*\PRINT share was added. Enter the time of the identified event in the format HH:MM:SS as your answer.
12:30:30

### Page 6
#### 1)By examining the logs located in the "C:\Logs\DLLHijack" directory, determine the process responsible for executing a DLL hijacking attack. Enter the process name as your answer. Answer format: _.exe
Dism.exe
#### 2)By examining the logs located in the "C:\Logs\PowershellExec" directory, determine the process that executed unmanaged PowerShell code. Enter the process name as your answer. Answer format: _.exe
Calculator.exe
#### 3)By examining the logs located in the "C:\Logs\PowershellExec" directory, determine the process that injected into the process that executed unmanaged PowerShell code. Enter the process name as your answer. Answer format: _.exe
rundll32.exe
#### 4)By examining the logs located in the "C:\Logs\Dump" directory, determine the process that performed an LSASS dump. Enter the process name as your answer. Answer format: _.exe
ProcessHacker.exe
#### 5)By examining the logs located in the "C:\Logs\Dump" directory, determine if an ill-intended login took place after the LSASS dump. Answer format: Yes or No
No
#### 6)By examining the logs located in the "C:\Logs\StrangePPID" directory, determine a process that was used to temporarily execute code based on a strange parent-child relationship. Enter the process name as your answer. Answer format: _.exe
WerFault.exe
