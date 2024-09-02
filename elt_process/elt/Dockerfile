# Utiliser l'image de base Python 3.8
FROM python:3.8-slim

# Mettre à jour les paquets et installer le client PostgreSQL version 16
RUN apt-get update && apt-get install -y wget gnupg2 lsb-release \
    && echo "deb http://apt.postgresql.org/pub/repos/apt/ $(lsb_release -cs)-pgdg main" > /etc/apt/sources.list.d/pgdg.list \
    && wget --quiet -O - https://www.postgresql.org/media/keys/ACCC4CF8.asc | apt-key add - \
    && apt-get update \
    && apt-get install -y postgresql-client-16 \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Copier le script ETL dans le conteneur
COPY elt_script.py .

# Commande pour exécuter le script ETL
CMD ["python", "elt_script.py"]