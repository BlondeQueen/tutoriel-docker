Challenge DevSecOps - Semaine 2 : Industrialisation & CI/CD
Objectif : Ne plus lancer les scans à la main. Tout doit s'exécuter automatiquement sur GitHub à chaque "Push" de code, et les rapports doivent être consultables sur le Web.

1. Initialisation du Dépôt (Git)
Action : Crée un dépôt privé sur GitHub.

Structure : Ton projet doit contenir ton docker-compose.yml (de la S1) et un nouveau dossier .github/workflows/.

Hygiène : Crée un fichier .gitignore pour exclure les rapports locaux (.html) et les dossiers inutiles.

2. Le Pipeline de Sécurité (GitHub Actions)
Crée un fichier .github/workflows/security.yml 
Ce pipeline doit s'exécuter sur une machine distante (Runner GitHub) et enchaîner ces étapes :

Checkout : Récupérer ton code(sur la main).

SCA Scan (Trivy) : Analyser l'image juice-shop avant de la lancer.

Contrainte : Le pipeline doit passer au ROUGE si une faille CRITICAL est trouvée.

DAST Scan (ZAP) : Lancer le scanner ZAP contre la cible.

Collecte : Récupérer les rapports générés (rapport.html et trivy.html).

3. Déploiement du Dashboard (GitHub Pages)
Au lieu de télécharger les rapports, nous allons les exposer sur le web.

Action : Utilise l'action JamesIves/github-pages-deploy-action pour envoyer tes rapports vers la branche gh-pages.

Exposition : Active GitHub Pages dans les réglages du repo pour rendre les rapports accessibles via une URL du type https://ton-pseudo.github.io/tutoriel-docker

Portail : Ajoute un petit fichier index.html à la racine de tes rapports pour naviguer facilement entre le rapport ZAP et le rapport Trivy.


Questions d'auto-validation :
Comment as-tu autorisé GitHub Actions à "écrire" sur ton propre dépôt pour publier la page ?

Pourquoi utilise-t-on la condition if: always() pour l'étape de génération du rapport ?

Si le scan Trivy bloque le pipeline (Fail), comment faire pour que le rapport soit quand même publié pour analyse ?
