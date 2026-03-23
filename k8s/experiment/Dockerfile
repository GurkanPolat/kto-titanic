FROM python:3.13-slim

# TODO : à remplir

# TODO : Mettre en place les trois arguments transmis par la CI/CD

# TODO : Les mettre en variables d'environnement pour que MlFlow focntionne correctement

# TODO : Ajouter les variables d'env techniques (pour créer les fichiers dans le répertoire tmp et pour le refresh git)

# TODO : Bien mettre en place le répertoire de travail

# TODO : Installer uv
# TODO : Copier les sources utiles

# TODO : Installer les dépendances et python avec uv

FROM python:3.13-slim

# Arguments de build pour les variables d'environnement
ARG MLFLOW_S3_ENDPOINT_URL 
ARG AWS_ACCESS_KEY_ID
ARG AWS_SECRET_ACCESS_KEY

# Définition des variables d'environnement pour l'accès à S3 via MLflow
ENV MLFLOW_S3_ENDPOINT_URL=${MLFLOW_S3_ENDPOINT_URL} \
    AWS_ACCESS_KEY_ID=${AWS_ACCESS_KEY_ID} \
    AWS_SECRET_ACCESS_KEY=${AWS_SECRET_ACCESS_KEY}

# Réduction des logs de GitPython
ENV GIT_PYTHON_REFRESH=quiet

# Définition du répertoire home pour les fichiers temporaires
ENV HOME=/tmp

# Définition du répertoire de travail dans le conteneur
WORKDIR /app

# Installation de UV (un gestionnaire de dépendances)
RUN pip install --no-cache-dir uv
# Copie des fichiers nécessaires pour installer les dépendances
COPY pyproject.toml uv.lock README.md ./
# Copie du code source nécessaire à l'exécution de l'expérience
COPY ./src/titanic/training ./src/titanic/training

# Installation des dépendances nécessaires à l'entrainement 
# définies dans le groupe training dans pyproject.toml
RUN uv sync -n --group training
