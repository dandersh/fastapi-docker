# fastapi-docker
This repo is for the TDD course for FastAPI and Docker found here: https://testdriven.io/courses/tdd-fastapi/

# Notes

## App Structure
- Routes are grouped by data group (summaries, etc.) with utility methods found in `crud.py`.
- Request/Reponse Models typed with `pydantic` 
- `Tortoise` orm initialized in `db.py`

## Useful Commands
- `source env/bin/activate` --> Activate virtual environment
- `uvicorn app.main:app --reload` --> Start the server and enable reload on file change
- `docker-compose up -d --build` --> Build a container in detached state
- `docker-compose down -v` --> Bring down all containers
- `docker-compose exec web-db psql -U postgres` --> Connect to web-db service and view postgres db
- `docker-compose exec web python -m pytest` --> Run all tests
- `docker-compose exec web black . --check --exclude="env"` --> Run black formatter while excluding dependencies found in `env` folder
- `docker-compose exec web isort . --skip="env"` --> Sort imports while excluding `env` folder contents