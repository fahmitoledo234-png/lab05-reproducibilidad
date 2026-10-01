FROM python:3.12-slim-bookworm

ENV PYTHONDONTWRITEBYTECODE=1 PYTHONUNBUFFERED=1 PIP_NO_CACHE_DIR=1

RUN groupadd --gid 1000 analista \
 && useradd --uid 1000 --gid analista --create-home analista

WORKDIR /app
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .
RUN mkdir -p salidas && chown -R analista:analista /app

USER analista
ENTRYPOINT ["python", "-c", "print('Proyecto listo. Análisis pendiente de implementar.')"]