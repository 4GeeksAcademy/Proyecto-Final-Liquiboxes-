FROM mcr.microsoft.com/devcontainers/python:0-3.10

ENV PYTHONUNBUFFERED 1

# Install PostgreSQL client
RUN apt-get update && export DEBIAN_FRONTEND=noninteractive \
    && apt-get -y install --no-install-recommends postgresql-client

# Install pipenv
RUN pip install pipenv

# Set work directory
WORKDIR /workspaces/${localWorkspaceFolderBasename}

# Copy Pipfile and Pipfile.lock from the root of the project
COPY ../Pipfile ../Pipfile.lock ./

# Install dependencies
RUN pipenv install --system --deploy

# We'll copy the rest of the code in the docker-compose file

# Command to run on container start
CMD ["sleep", "infinity"]