Pour commencer voici le lien du compte-rendu nextcloud



Importer l'image : docker pull nextcloud

Lancer la VM : docker run -d -p 80:80 nextcloud

Une fois réalisé, allez sur votre client Windows et installez : https://www.it-connect.fr/installer-nextcloud-sur-debian-11/

Ensuite, connectez-vous avec un utilisateur et le client va automatiquement synchroniser vos fichiers !

Vous pouvez ajouter des utilisateurs, ou aller dans les paramétres sur l'interface web de votre site : IP de votre serveur. dans l'onglet utilisateur, cependant, ils doivent avoir une adresse email et un groupe.

Il existe également un "market" pour installer des extensions, ce qui étend les possibilités grandement, avec du LDAP par exemple, du SSL, ou encore un FTP, voire du MFA.

Documentation : https://doc.nextcloud.com/desktop/next/advanced_usage/command_line_client.html

Réaliser un script de sauvegarde locale et compression.

D'abord, nous allons installer le client sur notre Linux en ligne de commande : Télécharger nextCloud pour Linux

Puis vous pouvez suivre les commandes et voilà ! Votre client va être installé. Maintenant, pour "importer" des fichiers de votre serveur, utilisez la commande suivante :
owncloudcmd -u USER -p PASSWORD FICHIER_LOCAL SERVEUR FICHIER (utilisez / pour tout synchroniser)

Dans notre exemple, je rentre la commande :

owncloudcmd -u admin -p admin -s --sync-hidden-files /home/nextcloud-syn/ http://192.168.20.76:80 toip

Pour le rendre automatique, je vais utiliser crontab.
La première ligne permet de rendre la sauvegarde automatique :
45 23 * * * bash /home/script.sh

