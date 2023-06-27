# Local Airflow
## Requirements

- [Python 3.10+](https://www.python.org/downloads/) 
- [Pip](https://pip.pypa.io/en/stable/getting-started/) or [Poetry](https://python-poetry.org)
- [Docker and Docker Compose](https://docs.docker.com/engine/install/)

## Install the dependencies

### Poetry

```sh
poetry install
```

### Pip

On Linux/WSL/Mac:

```sh
python -m venv .venv
source ./.venv/bin/activate
pip install -r requirements.txt
```

On Windows:

TODO

## Setup

1. Rename or copy the `.env.model` file to a `.env` file.
2. Activate your Python environment
   1. Venv:

   ```sh
   source ./.venv/bin/activate 
   ```

   2. Poetry:

   ```sh
   poetry shell
   ```

3. Generate a [Fernet Key](https://airflow.apache.org/docs/apache-airflow/stable/administration-and-deployment/security/secrets/fernet.html):
   1. After the virtualenv is activated enter python shell

   ```sh
   python
   ```

   2. Run this script

   ```python
   from cryptography.fernet import Fernet

   fernet_key = Fernet.generate_key()
   print(f"AIRFLOW__CORE__FERNET_KEY={fernet_key.decode()}")
   ```

    3. Copy the output to the `.env` file and replace the empty `AIRFLOW__CORE__FERNET_KEY` line
4. Run the docker compose, the `-d` flag runs the containers in the background.

    ```sh
    docker-compose up --build -d
    ```

    or depending on your docker version:

    ```sh
    docker compose up --build -d
    ``` 

5. Open the url http://localhost:8080 in the browser.

    ```
    user: airflow
    password: airflow
    ```

6. The sample DAG should appear on the Airflow UI.

## Video Instructions

TODO with [asciinema](https://asciinema.org)
