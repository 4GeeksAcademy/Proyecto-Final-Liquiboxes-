FROM python:3.10

ENV PYTHONUNBUFFERED 1

RUN apt-get update && apt-get install -y \
    postgresql-client \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /workspaces/${localWorkspaceFolderBasename}

COPY requirements.txt .
RUN pip install -r requirements.txt

CMD ["sleep", "infinity"]