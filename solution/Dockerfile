FROM python:3.12-slim

WORKDIR /app

# cette commande permet d'installer curl dans l'image docker puis nettoie les fichiers temporaires
#curl = outil permettant d'effectuer des requêtes HTTP/HTTPS, télécharger des fichiers ou interroger des API 
RUN apt-get update && apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

ENV MODEL_PATH=/app/model/ibm_attrition_model.joblib
ENV APP_ENV=production

CMD ["bash", "-lc", "uvicorn app:app --host 0.0.0.0 --port ${PORT:-10000}"]
