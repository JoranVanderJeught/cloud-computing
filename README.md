# Storingsmelder van Joran Van der Jeught

1. Stap 1: Clone git repo en ga in de map
``` bash 
git clone https://github.com/JoranVanderJeught/cloud-computing.git
cd cloud-computing
```

2. Stap 2: .env file aanmaken
``` bash 
cp .env.example .env
```
Vul de variabelen in, in de file

3. Stap 3: .env file aanmaken
``` bash 
docker compose up -d --build
```

4. Stap 4: Controleren of alles draait
``` bash
docker compose ps
```

5. Stap 5: De applicatie openen

Surf naar http://localhost:8000

## Wat ik gedaan heb

- Een **Dockerfile** die de applicatie bouwt op `python:3.14-slim`. De pakketten worden geïnstalleerd voor de code gekopieerd wordt, zodat de build sneller gaat.
- Een **compose.yaml** met twee services: `web` (de applicatie, op poort 8000) en `db` (PostgreSQL 18). De applicatie vindt de database op de naam `db`. Poort 5432 is niet gepubliceerd.
- Een **volume** `pgdata` op `/var/lib/postgresql`, zodat de meldingen een `docker compose down` overleven.
- De wachtwoorden staan in **.env**, dat in `.gitignore` staat. **.env.example** toont welke variabelen je moet invullen.
- Het image staat publiek op `ghcr.io/joranvanderjeught/storingsmelder:1.0`.