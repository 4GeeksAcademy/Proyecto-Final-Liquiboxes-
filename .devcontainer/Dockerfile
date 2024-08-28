FROM mcr.microsoft.com/devcontainers/python:3.10

ENV PYTHONUNBUFFERED 1

RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends postgresql-client

WORKDIR /workspaces

COPY requirements.txt .
RUN pip install -r requirements.txt

CMD ["sleep", "infinity"]