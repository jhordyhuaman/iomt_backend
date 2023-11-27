FROM python:3.9-slim

# Instalar gcc y otras dependencias necesarias
RUN apt-get update && apt-get install -y gcc python3-dev libpq-dev \
    && rm -rf /var/lib/apt/lists/*

COPY requirements.txt /tmp/requirements.txt
RUN pip3 install --no-cache-dir -r /tmp/requirements.txt

EXPOSE 5000
COPY . web/
WORKDIR web

CMD ["/usr/local/bin/gunicorn", "--config", "./gunicorn.conf.py"]