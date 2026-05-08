# Velociraptor

My initial experience with Velociraptor was challenging, as I had to understand how hunts, collections, and notebooks work, as well as how artifacts are used in investigations.

This section contains my notes, exercises, and reflections as I progressively improve my understanding of the tool and its use in a SOC environment.

## Question

### 1)Determine the registry key used for persistence and enter it as your answer.

I'm utilis artefact AUTORUN it's ok because utils to search process to strat sesion with windows
and utilised NoteBook for search into flow id autorun to collection and search with next practise reverse.exe 
I'm find 
HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\Run

### 2)Determine the folder that contains all Mimikatz-related files and enter the full path as your answer.

I'm search this folder, im's search all register im' found this in utilised artefefat serachYara
i'm find 
C:\Users\j0seph\AppData\Local\mimik

### 3)Determine the Microsoft Word document that j0seph recently accessed and enter its name as your answer. Answer format: _.DOCX
I'm search to docs and recently actived i use the artefact Windows.Registry.RecentDocs
I'm find 
insurance.DOCX

### 4)Visitez l'URL "https://127.0.0.1:8889/app/index.html#/search/all" et connectez-vous en utilisant les informations d'identification: admin/password. Après vous être connecté, cliquez sur le symbole circulaire adjacent à "Client ID". Par la suite, sélectionnez l'affichage "Client ID" et cliquez sur "Collecté". Lancez une nouvelle collection et rassemblez des artefacts étiquetés "Windows.KapeFiles.Targets" en utilisant la configuration _SANS_Triage. Enfin, examinez les artefacts recueillis et entrez le nom de la tâche planifiée qui commence par « A » et conclut par 'g' comme réponse.

I's search task and find 
AutorunsToWinEventLog
