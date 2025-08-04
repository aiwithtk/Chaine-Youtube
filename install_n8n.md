````md
# Setup d'un serveur n8n avec Docker et Ngrok

## Vérification de la version de Docker 
```bash
docker --version
````

### Vérification de Docker Compose

```bash
sudo docker compose version
```

## Installation de Docker avec Snap

```bash
sudo snap install docker
```

## Création d'un dossier pour sauvegarder toutes les données pertinentes de n8n

```bash
mkdir n8n-server
sudo chown -R 1000:1000 n8n-data/
sudo chmod -R 755 n8n-data/
```

## Installation de Ngrok

> Copier la ligne de commande depuis votre compte Ngrok.
> Exemple :

```bash
curl -sSL https://ngrok-agent.s3.amazonaws.com/ngrok.asc \
| sudo tee /etc/apt/trusted.gpg.d/ngrok.asc >/dev/null \
&& echo "deb https://ngrok-agent.s3.amazonaws.com bookworm main" \
| sudo tee /etc/apt/sources.list.d/ngrok.list \
&& sudo apt update \
&& sudo apt install ngrok
```

### Ajouter son Token dans la config Ngrok

```bash
ngrok config add-authtoken [YOUR_API_TOKEN] # Ajoutez votre clé API Ngrok
```

## Création d'un environnement pour les paramètres n8n

```bash
vim .env
```

### Contenu du fichier `.env`

```env
N8N_BASIC_AUTH_ACTIVE=true
N8N_BASIC_AUTH_USER=Admin #Choisissez votre USER
N8N_BASIC_AUTH_PASSWORD=admin123 # Choisissez votre mot de passe

N8N_HOST=[YOUR_IPV4_FROM_AWS_INSTANCE] #Copiez-collez votre adresse ipv4 de votre instance AWS
N8N_PORT=5678

N8N_COMMUNITY_PACKAGE_ALLOW_TOOL_USAGE=True

N8N_EDITOR_BASE_URL=[YOUR_LINK_NGROK] #Collez votre lien endpoint Ngrok
WEBHOOK_URL=[YOUR_LINK_NGROK] #Collez votre lien endpoint Ngrok

N8N_DEFAULT_BINARY_DATA_MODE=filesystem
NODE_ENV=production
```

## Création du fichier Docker Compose

```bash
vim docker-compose.yml
```

### Contenu du fichier `docker-compose.yml`

```yaml
services:
  n8n:
    image: n8nio/n8n
    restart: always
    container_name: n8n-server  # Nom personnalisé du conteneur
    ports:
      - "5678:5678"
    env_file:
      - .env
    volumes:
      - ./n8n-data:/home/node/.n8n
```

## Vérification des dossiers

```bash
ll
```

## Lancement de Docker

```bash
sudo docker compose up -d
```

## Vérification des permissions des conteneurs

```bash
sudo docker ps
```

## Activation du port 5678 (pare-feu UFW)

```bash
sudo ufw allow 5678
```

## Déploiement du lien n8n via Ngrok

```bash
ngrok http --url=[YOUR_LINK_NGROK] 5678
```
