# louisv-test-app

This is a simple Django application that serves a test page. It is containerized using Docker and includes a CI/CD pipeline to build and push the image to GitHub Container Registry.

## Prerequisites

- [Python 3.11+](https://www.python.org/)
- [Docker](https://www.docker.com/)

## Local Setup

1.  Clone the repository:
    ```bash
    git clone https://github.com/lsviennot/louisv-test-app.git
    cd louisv-test-app
    ```

2.  Create and activate a virtual environment:
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  Install dependencies:
    ```bash
    pip install -r requirements.txt
    ```

4.  Run migrations (optional for this simple app, but good practice):
    ```bash
    python manage.py migrate
    ```

5.  Run the development server:
    ```bash
    python manage.py runserver
    ```
    Access the app at `http://127.0.0.1:8000/`.

## Running with Docker

1.  Build the Docker image:
    ```bash
    docker build -t louisv-test-app .
    ```

2.  Run the container:
    ```bash
    docker run -p 8000:8000 louisv-test-app
    ```
    Access the app at `http://localhost:8000/`.

## CI/CD Pipeline

The project includes a GitHub Actions workflow (`.github/workflows/docker-image.yml`) that triggers on pushes to the `main` or `master` branch.

It performs the following steps:
1.  Check out the code.
2.  Log in to GitHub Container Registry (ghcr.io).
3.  Build the Docker image.
4.  Push the image to `ghcr.io/lsviennot/louisv-test-app:latest` (and tagged with the commit SHA).

