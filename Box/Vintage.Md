## Vintage 

#### 1)What tool did the attacker use to fuzz the web server ? (Format- include version e.g, nmap@7.80)

### a)Start my search 
http && tcp.ack == 0

#### b)http.user_agent and i find User-Agent: Fuzz Faster U Fool v2.1.0-dev

#### 2)Which subdomain did the attacker discover?

### a)Search this question dns , tls ...

### b)search ip.src_host && http && tcp.srport

and find cloud

### 3)How many login attempts did the attacker make before successfully logging in to the dashboard?

## a)I'm search not ok with access cloud 
Ce qui ma permet de determiner le sousdomaine qui a ete hack
Ftcp.ack == 1 && tcp.srcport && http 

[Full request URI: http://cloud.vantage.tech/dashboard/auth/login/]
http.user_agent == "Fuzz Faster U Fool v2.1.0-dev"

Avant le paquet 26081

http.request.version == "HTTP/1.1"  && http.user_agent == "Fuzz Faster U Fool v2.1.0-dev"

Fuzz Faster sert juste a determiner si c'est un sous domaine !

Il a reussis au bout de la 4 em fois 
On peut donc mettre 3 
Avec un simple requete qui est 
http.request.method == POST && ip.src == 117.200.21.26


### 4)When did the attacker download the OpenStack API remote access config file? (UTC) 

J ai juste fait une recherche sur apre ca connexion et regarder get api/acces
VOicic la commande 
frame.number > 21091 && ip.src == 117.200.21.26

La reponse est 
2025-07-01 09:40:29

## 5)When did the attacker first interact with the API on controller node? (UTC)
ip.src

Je suis passer sur le fichier controller et par la suite 
ip.src == 117.200.21.26 && tcp.ack == 1

Ce qui m'a permit de trouver 
2025-07-01 09:41:44


### 5)  What is the project id of the default project accessed by the attacker
J ai commencer par suivre cette requete
ip.src == 117.200.21.26 && tcp.ack == 1 && http.request.method ==POST

ET j;ait remarquer un post.identity/v3/users
Et donc l'id etait la 

### 6)Which OpenStack service provides authentication and authorization for the OpenStack API?

Tous s'effectue sur cette ligne POST /identity/v3/auth/tokens HTTP/1.1
Le service catalogue est keystone

### 7)What is the endpoint URL of the swift service?
J'ai du recher en follow http une requete post dans laquelle y avait swift a la suite de ca j'ai juste eu besoin de prendre l'ur
ip.src == 117.200.21.26&& http.request.method ==POST
ip.src == 117.200.21.26&& http.request.method ==POST

### 8)How many containers were discovered by the attacker?

Dans cette question il faut commencer a lister les containers qui on ete lister parl'attaquant je ne vois pas comment faire pour le momment 
http.request.uri contains "/v1/AUTH"
IL faut lister out authentification qui ont ete faites pour determiner combien de containers on ete accesible 

### 9)When did the attacker download the sensitive user data file? (UTC)

ip.src == 117.200.21.26 && http.request.method == "GET"

16398	476.212102	117.200.21.26	134.209.71.220	HTTP	543	GET /v1/AUTH_9fb84977ff7c4a0baf0d5dbb57e235c7/user-data/user-details.csv HTTP/1.1 

### 10)How many user records are in the sensitive user data file?
Just folow this and copi coll to and find 28

### 11)

On peut considerer que l'attaquant a d'abords tester tout les ports avec fufu 
Pour ensuite essayer de passer avec le mots de passe 

