FROM python:2.7-slim

RUN sed -i 's/deb.debian.org/archive.debian.org/g' /etc/apt/sources.list && \
    sed -i 's/security.debian.org/archive.debian.org/g' /etc/apt/sources.list && \
    sed -i '/buster-updates/d' /etc/apt/sources.list && \
    apt-get update && \
    apt-get install -y --allow-unauthenticated \
        git \
        build-essential \
        libssl-dev \
        libffi-dev \
        libdb-dev \
        python-dev && \
    rm -rf /var/lib/apt/lists/*

RUN git clone https://github.com/cryoem/emen2.git /app/emen2

WORKDIR /app/emen2

# Dependências compatíveis com Python 2.7
RUN pip install --no-cache-dir \
    "setuptools<45" \
    "pip<21" \
    typing \
    incremental==17.5.0

# Berkeley DB + dependências do EMEN2
ENV BERKELEYDB_DIR=/usr

RUN pip install --no-cache-dir \
    automat==0.8.0 \
    twisted==17.9.0 \
    zope.interface==4.7.2 \
    "jsonrpc>=0.99a0,<1.0" \
    mako==1.1.0 \
    python-dateutil==2.8.2 \
    markdown==3.1.1 \
    bsddb3==6.2.9

# Instalar o EMEN2
RUN python setup.py install

# Diretório do banco
ENV EMEN2DBHOME=/app/emen2db

EXPOSE 8080

# Criar o ambiente Berkeley DB e iniciar o servidor
CMD ["sh", "-c", "emen2ctl create -h /app/emen2db && emen2ctl start -h /app/emen2db --port=8080 && tail -f /dev/null"]
