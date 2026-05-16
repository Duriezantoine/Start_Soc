## Box01

### 1)Question:
What is the likely IPv4 address of someone from the Po1s0n1vy group scanning imreallynotbatman.com for web application vulnerabilities?

#### a)Premier box de ce type j'ai commencer a emenunerer tout les sources types qui me permettrait de resoudre le bot 
index=botsv1 
|stats count by sourcetype

Pour la premiere question je me suis concentree sur sourcetpe=stream:http

  Ce qui m a le plus fait tiquer 
  C'est a la suite de cette commande 
  index=botsv1 sourcetype=stream:http
  |stats count by src_ip
  |table cout, src_ip

210  210	169.229.3.91
810 818	192.168.2.50

Ce n'etait pas suffisant pour me permettre de repondre a la question j'ai changer ma requete en 
index=botsv1  sourcetype=stream:http
|search "imreallynotbatman.com"
| stats count by src_ip
|table count , src_ip

Ce qui a donnee la reponse 
	40.80.148.42

### 2)Question:
What content management system is imreallynotbatman.com likely using?
Answer guidance: Please do not include punctuation such as . , ! ? in your answer. We are looking for alpha characters only.

A la base je voulais chercher les requetes une par une dns http ou autre que je ne connais a la suite de cette commande 
index=botsv1  sourcetype=stream:http src_ip="40.80.148.42"
J'ai trouver une requete http qui me donner ca requetes avec url 
jomla 

### 3)Question:
This attack used dynamic DNS to resolve to the malicious IP. What fully qualified domain name (FQDN) is associated with this attack?

J'ai commencer a faire cette premiere requete
index=botsv1  sourcetype=stream:http src_ip="40.80.148.42"
|stats count by uri
|table count, uri

Pour repondre a cette question j'ai premierement commencer a changer le sourcetype
je suis passer sur sourcetype=stream:dns
A la suite de ca je suis parti sur une commande 

index=botsv sourcetype=strea:dns
|table query 

Ce qui m'a donner une longue liste a la suite je suis parti rechercher tout les services dns dynamique 
Mais ce n'etait pas ca 
dynect

J'ai donc devoile l'indice 
Consider the answer to question 104. The fully qualified domain name was recorded by Stream, Suricata, and the Fortigate firewall.

Quel FQDN est associé à une attaque utilisant DNS dynamique ?”=== qu'elle dommaine 

Je n'ai pas reussi cette question, 
A fallait prendre l'adresse du server pour ensuite aller rechercher directement dans src_header
