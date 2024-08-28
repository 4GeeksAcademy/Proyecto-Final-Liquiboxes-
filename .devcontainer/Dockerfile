FROM mcr.microsoft.com/devcontainers/python:0-3.10

ENV PYTHONUNBUFFERED 1

# Instalar dependencias del sistema
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends \
        postgresql-client \
        libpq-dev \
        git \
        curl \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Instalar pipenv
RUN pip install --no-cache-dir pipenv

# Instalar Node.js
RUN curl -fsSL https://deb.nodesource.com/setup_lts.x | bash - \
    && apt-get install -y nodejs \
    && apt-get clean \
    && rm -rf /var/lib/apt/lists/*

# Establecer el directorio de trabajo
WORKDIR /workspaces

# Copiar los archivos de requisitos e instalar dependencias
COPY Pipfile Pipfile.lock ./
RUN pipenv install --system --deploy

# Si prefieres usar requirements.txt en lugar de Pipfile, descomenta estas líneas:
# COPY requirements.txt .
# RUN pip install --no-cache-dir -r requirements.txt

# Copiar el resto de los archivos del proyecto
COPY . .

# Comando por defecto al iniciar el contenedor
CMD ["sleep", "infinity"]