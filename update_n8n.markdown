# Mise à jour de n8n sur une instance Docker (Ubuntu/AWS)

Ce guide explique comment mettre à jour une instance **n8n** auto-hébergée sur une machine virtuelle Ubuntu (AWS) utilisant Docker, Docker Compose, et Ngrok, tout en préservant vos données (workflows, credentials, etc.).

## Pré-requis
- Accès SSH à votre VM Ubuntu avec privilèges `sudo`.
- Configuration Docker avec un volume persistant (`n8n-data`).
- Sauvegarde des données avant toute mise à jour.
- Fichier `docker-compose.yml` et `.env` configurés dans le dossier `~/n8n-server`.

## Étapes pour la mise à jour

### 1. Sauvegarder vos données
Pour éviter toute perte de données, sauvegardez le dossier `n8n-data`.

1. **Arrêtez le conteneur n8n** :
   ```bash
   cd ~/n8n-server
   sudo docker compose down
   ```

2. **Sauvegardez le dossier `n8n-data`** :
   ```bash
   cp -r ~/n8n-server/n8n-data ~/n8n-server/n8n-data-backup-$(date +%Y%m%d)
   ```

3. **Vérifiez la sauvegarde** :
   ```bash
   ls -l ~/n8n-server
   ```
   Vérifiez que le dossier `n8n-data-backup-YYYYMMDD` existe.

### 2. Consulter les notes de version
Vérifiez les **notes de version** sur le [dépôt GitHub de n8n](https://github.com/n8n-io/n8n/releases) pour identifier les éventuels changements cassants ou instructions spécifiques.

### 3. Mettre à jour les packages du serveur
Assurez-vous que votre système est à jour :
```bash
sudo apt-get update
sudo apt-get upgrade -y
```

### 4. Mettre à jour l'image Docker de n8n
1. **Naviguez vers le dossier du projet** :
   ```bash
   cd ~/n8n-server
   ```

2. **Téléchargez la dernière image n8n** :
   ```bash
   sudo docker compose pull
   ```
   Cela récupère la dernière version de l'image `n8nio/n8n`. Pour une version spécifique (ex. `1.106.3`), modifiez `docker-compose.yml` :
   ```yaml
   services:
     n8n:
       image: n8nio/n8n:1.106.3
       restart: always
       container_name: n8n-server
       ports:
         - "5678:5678"
       env_file:
         - .env
       volumes:
         - ./n8n-data:/home/node/.n8n
   ```

### 5. Redémarrer le conteneur
1. **Relancez le conteneur** :
   ```bash
   sudo docker compose up -d
   ```

2. **Vérifiez que le conteneur fonctionne** :
   ```bash
   sudo docker ps
   ```

### 6. Vérifier la version de n8n
1. **Via l'interface web** :
   - Accédez à votre instance via l'URL Ngrok (ex. `https://votre-lien-ngrok.io`).
   - Connectez-vous avec vos identifiants (ex. `Admin`/`admin123`).
   - Vérifiez la version dans les **Settings** ou le tableau de bord.

2. **Via la ligne de commande** (optionnel) :
   ```bash
   sudo docker exec n8n-server n8n --version
   ```

### 7. Vérifier les logs
Vérifiez les logs pour détecter d'éventuelles erreurs :
```bash
sudo docker logs n8n-server
```

### 8. Mettre à jour Ngrok (si nécessaire)
Si l'URL Ngrok a changé, mettez à jour le fichier `.env`.

1. **Relancez Ngrok** :
   ```bash
   ngrok http 5678
   ```
   Notez la nouvelle URL (ex. `https://abcd1234.ngrok.io`).

2. **Mettez à jour `.env`** :
   ```bash
   vim .env
   ```
   Modifiez :
   ```env
   N8N_EDITOR_BASE_URL=https://abcd1234.ngrok.io
   WEBHOOK_URL=https://abcd1234.ngrok.io
   ```

3. **Redémarrez n8n** :
   ```bash
   sudo docker compose down
   sudo docker compose up -d
   ```

### 9. Tester vos workflows
- Connectez-vous à l'interface n8n.
- Testez vos workflows pour vérifier leur bon fonctionnement.
- Consultez les notes de version si des nœuds ou configurations ont changé.

### 10. Nettoyer les anciennes images (optionnel)
Libérez de l'espace en supprimant les images Docker inutilisées :
```bash
sudo docker image prune
```

## Résolution des problèmes
- **Erreur ENOTEMPTY** :
  ```bash
  sudo rm -rf /usr/lib/node_modules/.n8n-*
  sudo docker compose pull
  ```
- **Problèmes Ngrok** : Vérifiez que le port 5678 est accessible et relancez Ngrok.
- **Erreur de connexion AWS** : Assurez-vous que le groupe de sécurité AWS autorise le port 5678.
- **Données manquantes** : Restaurez la sauvegarde depuis `n8n-data-backup-YYYYMMDD`.

## Conseils
- Mettez à jour n8n régulièrement (mensuellement) pour éviter les sauts de version.
- Testez la mise à jour dans un environnement de staging si possible.
- Surveillez les logs pendant quelques jours après la mise à jour.

Pour toute question, consultez la [documentation officielle](https://docs.n8n.io) ou ouvrez une issue sur [GitHub](https://github.com/n8n-io/n8n).