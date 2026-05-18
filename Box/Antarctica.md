
## Antartctica

##2)The malware creates a lock on a file to ensure that only one instance of it is running. What is the full path of that file?
POur la mise en place en place de cette 2 question je dois donc fair une analyse dynamique du logiciel 
POur y arriver
1)Iso kalo
2)Mise en place de volatity 
3)Ce qui est demander dans la question est qu'est ce qui a ete a la suite de l'execution de ce malwqre je peux donc utiliser une de ces commandes

a)Commande qui permet de determiner tout les fichier qui se cree
inotifywait -m /tmp si ca ne prends rien inotifywait m -r ¬

b)Determinere si un programme se lance 
watch -n 1 ps aux  

c)Voir les fichier ouvert par un programme 

d)Voir toutes les action d'un programme 
strace -f -0 log.txt ./programme

e)Determiner si il y a une connexion sur le reseaux
ss -tup 
tcpdump
