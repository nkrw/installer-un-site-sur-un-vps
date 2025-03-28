**Formation : Héberger un site PHP sur un VPS avec Apache et Termius (SFTP)**

---

# **1. Introduction**
## Objectifs de la formation :
- Apprendre à héberger un site PHP sur un VPS
- Installer et configurer Apache, PHP et MySQL
- Utiliser Termius pour la connexion SSH et le transfert de fichiers via SFTP
- Sécuriser l'hébergement avec Cloudflare

---

# **2. Configuration du VPS**
## Connexion au VPS avec Termius
1. Installer **Termius** sur votre PC
2. Ajouter une nouvelle connexion SSH avec :
   - **Host** : Adresse IP du VPS
   - **Username** : root
   - **Password / Clé SSH**
3. Se connecter et mettre à jour le serveur :
```bash
sudo apt update && sudo apt upgrade -y
```

---

# **3. Installation d'Apache et PHP**
## Installer Apache
```bash
sudo apt install apache2 -y
```
- Vérifier l'installation : http://IP-DU-VPS
- Démarrer Apache si nécessaire :
```bash
sudo systemctl enable apache2
sudo systemctl start apache2
```

## Installer PHP et MySQL
```bash
sudo apt install php libapache2-mod-php -y
```
- Installer les modules PHP supplémentaires :
```bash
sudo apt install php-cli php-gd php-mysql -y
```
- Vérifier PHP :
```bash
php -v
```
- Installer MySQL :
```bash
sudo apt install mariadb-server -y
sudo mysql_secure_installation
```

---

# **4. Copier des fichiers sur le VPS avec Termius (SFTP)**
## Méthode : Interface graphique SFTP (Termius)
1. Ouvrir Termius et se connecter au VPS en tant que root
2. Aller dans **"SFTP"**
3. Glisser-déposer les fichiers directement dans `/var/www/html/`

## Définir les permissions des fichiers :
```bash
sudo chown -R www-data:www-data /var/www/html/
sudo chmod -R 755 /var/www/html/
```

---

# **5. Sécuriser le VPS avec Cloudflare**
## Configurer Cloudflare pour activer HTTPS
1. Ajouter votre domaine sur Cloudflare
2. Configurer les enregistrements DNS pour pointer vers l'IP du VPS
3. Activer le mode **"Full (strict)"** SSL/TLS
4. Forcer la redirection HTTPS dans les paramètres de Cloudflare

---

# **6. Conclusion**
- Votre site PHP est maintenant hébergé sur un VPS
- Utilisation de Termius pour la connexion et le transfert de fichiers
- Sécurisation avec Cloudflare
- Possibilité d'optimiser avec un gestionnaire de déploiement (Git, CI/CD, etc.)

📌 **Bonus : Automatiser le déploiement avec Git !**

