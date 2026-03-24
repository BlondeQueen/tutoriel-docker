Challenge DevSecOps: Lab Local
Objectif: Faire communiquer un scanner et une cible via Docker.

1. Déploiement (Docker Compose)
Cible : Image bkimminich/juice-shop (App vulnérable).
Scanner : Image ghcr.io/zaproxy/zaproxy:stable (Outil d'audit).

Contrainte : Utiliser un réseau bridge commun et un volume pour récupérer le rapport .html sur ton PC.

2. Audit & Logs
Logs : Affiche les logs de la cible en temps réel (docker logs -f).

Interactivité : Entre dans le container du scanner (docker exec -it) pour explorer l'environnement.

3. Test de Communication
Depuis le container Scanner, tente de joindre la Cible :

Ping : ping CONTAINER_CIBLE

HTTP : curl -I http://CONTAINER_CIBLE:3000
Note : localhost ne fonctionnera pas entre containers.

Questions d'auto-validation
- Pourquoi localhost échoue-t-il ici ?
- À quoi sert précisément le volume dans ce test ?
- Comment Docker résout-il le nom de la cible sans adresse IP fixe ?
