# Réseau - Résumé

## Modèle OSI

Le modèle OSI (Open Systems Interconnection) divise les communications en sept couches, chacune avec son propre rôle spécifique.

1. **Couche Physique :** Transmission de bits sur le support physique.
2. **Couche Liaison de données :** Gestion des erreurs et du flux de données.
3. **Couche Réseau :** Routage des données à travers le réseau.
4. **Couche Transport :** Gestion du contrôle de flux et de la fiabilité de la transmission.
5. **Couche Session :** Établissement, gestion et fermeture des sessions de communication.
6. **Couche Présentation :** Conversion des données entre le format réseau et l'application.
7. **Couche Application :** Interface utilisateur et services d'application.

## Protocoles Réseau

- **TCP (Transmission Control Protocol):** Protocole orienté connexion, fiable et garantissant la livraison des données.
- **UDP (User Datagram Protocol):** Protocole non orienté connexion, rapide, mais sans garantie de livraison.
- **IP (Internet Protocol):** Protocole pour le routage des paquets sur le réseau.
- **HTTP (Hypertext Transfer Protocol):** Protocole de communication pour le World Wide Web.
- **DNS (Domain Name System):** Convertit les noms de domaine en adresses IP.

## Adresses
-  **@IP (Internet Protocol):** Etiquette numérique attribuée à chaque périphérique sur un réseau.
    - IPv4 (32 bits) ou IPv6 (128 bits).
    - Exemple: `192.168.1.1/16`
    - Se compose d'une partie réseau et d'une partie hôte. Le nombre de bit représentant le réseau est défini par le masque.
    - Souvent suivi et utilisé avec un numéro de port qui désigne le logiciel cible (80 pour HTTP par exemple).
- **@MAC (Media Access Control):** Identifiant physique unique attribué à chaque carte réseau.
    - Exemple: `00:1A:2B:3C:4D:5E`
    - Se compose d'une partie constructeur et d'une partie unique. Moitié-moitié.
- **@ Symbolique:** Addresse IP sous format textuel plus convivial à retenir et écrire.
    - Exemple: `www.univ-lr.fr`
    - Résolu par le serveur DNS qui le transforme en adresse IP.
    - Peut être un **FQDN**, une forme complète d'adresse symbolique qui suit la structure hiérarchique du DNS et permet une identification précise d'une ressource sur Internet.

## Calculs

### Unités

- bit, octet (8 bits) ou mot de données (2n octets)  
- Unités binaires : kibi (Ki) = 2^10, mébi (Mi) = 2^20, gibi (Gi) = 2^30… (norme)  
- Unités décimales : kilo (k) = 10^3, méga (M) = 1^6, giga (G) = 10^9… (usage)

### Débit

>Le débit (D) mesure la quantité de données transférées par unité de temps.

`debit[bits/s] = data[bits] / temps[s]`

### Temps de Propagation

>Le temps de propagation représente le temps pour qu'un bit traverse la distance entre l'émetteur et le récepteur.

`tp[s] = distance[m] / vitessePropagation[m/s]`

### Efficacité

>L'efficacité mesure la proportion du réseau utilisé pour de l'utile (des données concètes) comparé au total.

`efficacité = utile / total`
- utile : en général les données utiles (données à transférer)  
- total : en général toutes les données (incluant les surcharges protocolaires
tels que les entêtes et/ou les acquittements)

## Principaux protocoles de communication

### Telnet

`telnet [adresse_ip] [port]
`

> Protocole de communication non sécurisé utilisé pour l'accès à distance à des systèmes. Les données sont transmises en texte clair. Utilisé en spécifiant l'adresse IP et le port du serveur mais pas sécurisé. Permet des requêtes HTTP.

### SSH (Secure Shell)

`ssh [utilisateur]@[adresse_ip]`

> Protocole sécurisé permettant une connexion chiffrée et sécurisée à distance. Souvent utilisé pour l'accès et la gestion à distance. Utilisé en spécifiant l'utilisateur et l'adresse IP du serveur.

### FTP (File Transfer Protocol)

`ftp [adresse_ip]`

> Protocole de transfert de fichiers non sécurisé permettant le transfert de fichiers entre un client et un serveur. Utilisé en spécifiant l'adresse IP du serveur. Simple mais pas sécurisé.

### SFTP (Secure File Transfer Protocol)

`sftp [utilisateur]@[adresse_ip]`

> Protocole sécurisé de transfert de fichiers utilisant SSH pour l'authentification et le chiffrement. Utilisé en spécifiant l'utilisateur et l'adresse IP du serveur.

## Topologie réseau

La topologie d'un réseau définit la manière dont les dispositifs sont physiquement ou logiquement connectés les uns aux autres. Voici quelques topologies couramment utilisées :

### Topologie en Étoile

>Tous les dispositifs sont connectés à un concentrateur central (hub) ou un commutateur.
  
- **Avantages :** Facilité de gestion, détection simple des erreurs.

- **Inconvénients :** Dépendance envers le concentrateur ou le commutateur central.

### Topologie en Bus

> Tous les dispositifs partagent une ligne de communication commune.

- **Avantages :** Simplicité de configuration, coût réduit pour un petit nombre de dispositifs.

- **Inconvénients :** La défaillance d'un nœud peut affecter tout le réseau.

### Topologie en Anneau

> Chaque dispositif est connecté à exactement deux autres, formant un cercle.

- **Avantages :** Transmission de données uniforme, peu de collisions.

- **Inconvénients :** La défaillance d'un nœud peut interrompre le réseau.

## Protocole HTTP

Utilisé pour le transfert de données sur le World Wide Web. Il définit les règles pour la transmission d'informations (texte, photos, vidéos...) entre les serveurs web et les navigateurs web.
- **Sans État (Stateless) :** Chaque requête du client est traitée indépendamment, sans connaissance de l'état précédent.

- **Basé sur le Texte :** Les messages HTTP sont généralement en texte brut, ce qui facilite la compréhension et le débogage.

- **Modèle de Requête/Réponse :** La communication est établie par l'envoi de requêtes par le client et les réponses correspondantes du serveur.

- **HTTPS:** Utilise une couche de chiffrement TLS/SSL pour sécuriser les communications entre le client et le serveur.

### Méthodes HTTP

- **GET :** Récupère des données spécifiées à partir d'une ressource.
- **POST :** Soumet des données pour être traitées afin de créer une nouvelle ressource.
- **PUT :** Met à jour ou crée une ressource spécifique.
- **DELETE :** Supprime une ressource spécifique.
- **HEAD :** Récupère les en-têtes d'une ressource sans récupérer son corps.

### En-têtes HTTP

Les en-têtes HTTP fournissent des informations supplémentaires dans la requête ou la réponse, telles que le type de contenu, la date, et les cookies.

### Statut de Réponse HTTP

Les codes de statut indiquent le résultat de la requête. Quelques exemples :

- **200 OK :** La requête a réussi.
- **404 Not Found :** La ressource demandée n'a pas été trouvée.
- **500 Internal Server Error :** Erreur interne du serveur.

## Commandes de Base du Réseau

| Commande      | Options Principales         | Utilité                                                  |
|---------------|-----------------------------|----------------------------------------------------------|
| `ping`        | `-c [count]`                | Tester la connectivité en envoyant un nombre de paquets.  |
| `nslookup`    |              | Obtenir des informations DNS spécifiques. Permet de résoudre une adresse (@IP <-> FQDN)   |
| `ifconfig`    | `interface`                 | Afficher ou configurer les paramètres d'une interface réseau spécifié (ou toutes).    |
| `traceroute`  | `-n`                        | Suivre l'itinéraire sans résoudre les adresses IP.        |
| `netstat`     |  | Afficher les connexions et les statistiques réseau.        |


## Serveur Web Apache2

> Un serveur web est un logiciel qui répond aux demandes des navigateurs en fournissant des pages et des contenus via HTTP. Il facilite l'accès aux sites internet en agissant comme une interface entre les utilisateurs et les fichiers stockés sur le serveur.

### Installation

Sur Ubuntu/Debian :
```bash
sudo apt-get update
sudo apt-get install apache2
```

### Fichiers de Configuration Principaux
1. `/etc/apache2/apache2.conf` : Fichier principal de configuration d'Apache2. Il contient des directives globales pour le serveur.
2. `/etc/apache2/sites-available/` : Répertoire contenant les fichiers de configuration des sites virtuels. Ces fichiers définissent la configuration spécifique à chaque site hébergé.
3. `/etc/apache2/sites-enabled/` : Répertoire contenant des liens symboliques vers les fichiers de configuration des sites virtuels activés. Ces liens sont créés à partir de sites-available pour activer les sites.

### Informations:
- **Port par Défaut** : Apache2 écoute généralement sur le port 80 pour les requêtes HTTP et sur le port 443 pour les requêtes HTTPS.
- **Répertoire Racine** : Le répertoire où sont stockés les fichiers du site web par défaut est /var/www/html/.
- **Logs** : Les fichiers de journalisation se trouvent généralement dans le répertoire /var/log/apache2/.
- **Sécurité** : Des directives telles que Allow, Deny, et Require sont utilisées pour contrôler l'accès aux ressources du serveur.

### Principales Directives de Configuration
- **`DocumentRoot` :** : Indique le répertoire racine des documents servis par Apache2.
- **`Directory` :** : Définit les directives spécifiques au répertoire, telles que les autorisations et les options.
- **`VirtualHost` :** : Permet la configuration de plusieurs sites sur le même serveur, chacun avec son propre ensemble de paramètres.
- **`ServerName` :** Définit le nom d'hôte principal du serveur. Utile pour les configurations de virtual hosts.
- **`ServerAdmin` :** Spécifie l'adresse e-mail de l'administrateur du serveur. Les messages d'erreur du serveur peuvent être envoyés à cette adresse.
- **`ErrorLog` :** Indique le fichier de journal où les messages d'erreur du serveur sont enregistrés.
- **`CustomLog` :** Spécifie le fichier de journal pour les accès au serveur. Il peut être configuré pour enregistrer différentes informations telles que les adresses IP, les requêtes, etc.
- **`Directory` :** Permet de configurer des options spécifiques à un répertoire particulier.

## Modèle en Couches et Analyses de Trame

### Modèle en Couches

Le modèle en couches divise les fonctionnalités de communication en différentes couches chacune responsable d'une tâche spécifique, ce qui facilite la conception, le développement et le dépannage des réseaux. Les principaux modèles en couches comprennent :

- **Modèle OSI (Open Systems Interconnection) :** Divise les fonctionnalités réseau en sept couches, de la couche physique à la couche application.

- **Modèle TCP/IP :** Plus communément utilisé, il se compose de quatre couches : la couche d'accès réseau, la couche Internet, la couche transport et la couche application.

![OSI vs TCP/IP](https://www.guru99.com/images/1/102219_1135_TCPIPvsOSIM1.png)

### Protocoles Courants

- **HTTP (Hypertext Transfer Protocol) :** Utilisé pour le transfert de pages web et d'autres ressources sur Internet.

- **TCP (Transmission Control Protocol) :** Protocole de transport fiable utilisé pour établir des connexions et garantir la livraison des données.

- **IP (Internet Protocol) :** Protocole de la couche Internet responsable du routage des paquets entre les hôtes sur un réseau.

- **DNS (Domain Name System) :** Convertit les noms de domaine en adresses IP pour permettre la résolution d'adresses.

- **Ethernet :** Protocole de la couche d'accès réseau utilisé pour la transmission de données sur un réseau local.

- **ARP (Address Resolution Protocol) :** Protocole de résolution d'adresses utilisé pour associer une adresse IP à une adresse MAC.

- **ICMP (Internet Control Message Protocol) :** Protocole utilisé pour envoyer des messages de contrôle et de diagnostic entre les hôtes IP.

- **FTP (File Transfer Protocol) :** Protocole utilisé pour le transfert de fichiers entre un client et un serveur sur un réseau TCP/IP.

- **SSH (Secure Shell) :** Protocole sécurisé pour l'accès à distance et le transfert de fichiers sur un réseau.

- **Telnet :** Protocole de communication non sécurisé utilisé pour l'accès à distance à des systèmes.

### Analyses de Trame

Les analyses de trame sont utilisées pour inspecter le trafic réseau et diagnostiquer les problèmes. Les outils d'analyse de trame tels que Wireshark permettent d'intercepter, d'examiner et d'enregistrer le trafic réseau pour identifier les anomalies, les erreurs de configuration et les attaques potentielles. Les analyses de trame peuvent fournir des informations détaillées sur les protocoles utilisés, les adresses source et de destination, les données transmises et d'autres métadonnées réseau.

## Adressage et Routage IP

> [!NOTE]
>Dans un réseau, les informations circulent entre les différents appareils. Lorsqu'un périphérique, envoie des données vers un autre périphérique, les données sont encapsulées dans des trames qui contiennent à la fois l'adresse IP de destination et l'adresse MAC de destination. Ces trames sont ensuite transmises via le réseau, en passant par les commutateurs, les routeurs et autres appareils réseau, jusqu'à atteindre le périphérique de destination. À chaque étape, les appareils réseau utilisent les adresses MAC pour acheminer les trames au bon périphérique sur le réseau local, tandis que les adresses IP sont utilisées pour le routage entre les réseaux.

### Adressage IP

L'adressage IP est un système de numérotation utilisé pour identifier chaque périphérique connecté à un réseau TCP/IP. 

|Classe|	Plage d'adresses|	Adresse réseau|	Adresse hôte	|Masque de sous-réseau par défaut	|Plage d'adresses privées	|Masque de sous-réseau privé
|-|-|-|-|-|-|-|
A|	1.0.0.1 à 126.255.255.254 Premier octet (1 à 126)| Trois derniers octets (0 à 255)| 255.0.0.0|	10.0.0.0 à 10.255.255.255|	255.0.0.0
B|	128.0.0.1 à 191.255.255.254	Deux premiers octets (128 à 191)|	Deux derniers octets (0 à 255)|	255.255.0.0|	172.16.0.0 à 172.31.255.255|	255.240.0.0
C|	192.0.0.1 à 223.255.255.254	Trois premiers octets (192 à 223)|	Dernier octet (0 à 255)|	255.255.255.0|	192.168.0.0 à 192.168.255.255|	255.255.255.0
D|	224.0.0.0 à 239.255.255.255|	-|	-|	-|	-|	-|
E|	240.0.0.0 à 255.255.255.254|	-|	-|	-|	-|	-|

## Routage IP

- **Table de Routage :** Une table utilisée par les routeurs pour déterminer le chemin optimal vers une destination donnée. Elle contient des informations sur les réseaux voisins et les chemins vers les destinations distantes.

## Utilité de l'Adresse MAC par Rapport à l'Adresse IP

> L'adresse MAC (Media Access Control) est une adresse physique unique attribuée à chaque carte réseau. Elle est utilisée pour identifier de manière unique les périphériques sur le réseau local. Lorsque des données sont envoyées sur le réseau local, les commutateurs utilisent les adresses MAC pour acheminer les trames vers le périphérique de destination. L'adresse IP, en revanche, est utilisée pour acheminer les données entre les réseaux et identifier de manière unique chaque périphérique sur Internet.

## Sous-Réseaux et Masques de Sous-Réseau

Les sous-réseaux permettent de diviser un réseau IP en segments plus petits pour une gestion et une organisation efficaces. Les masques de sous-réseau sont utilisés pour déterminer quels bits d'une adresse IP appartiennent à l'adresse du réseau et quels bits identifient des hôtes spécifiques sur ce réseau.

- **Masque de Sous-Réseau :** Une série de bits utilisée pour déterminer les parties de l'adresse IP qui représentent le réseau et les parties qui représentent les hôtes.

- **CIDR (Classless Inter-Domain Routing) :** Une méthode d'adressage IP qui permet une allocation plus efficace des adresses IP en utilisant des préfixes de réseau de longueur variable.