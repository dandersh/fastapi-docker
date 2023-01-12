# fastapi-docker
This repo is for the TDD course for FastAPI and Docker found here: https://testdriven.io/courses/tdd-fastapi/

![Continuous Integration and Delivery](https://github.com/dandersh/fastapi-docker/workflows/Continuous%20Integration%20and%20Delivery/badge.svg?branch=main)


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
- `docker-compose exec web python -m pytest --cov="."` --> Check test cover of app
- `docker-compose exec web flake8 .` --> Run flake8 linter
- `docker-compose exec web black . --check` --> See what files will be reformated
- `docker-compose exec web black .` --> Reformat files all files
- `docker-compose exec web black . --exclude="env"` --> Reformat files excluding those in the `env` folder
- `docker-compose exec web pytest -k "unit" -n auto` --> Run integration and unit tests concurrently

## TDD approach
- Add tests for happy path and error to `test_summaries.py`
- Run them and watch them fail
- Add route to `summaries.py`
- Add or update function in `crud.py`

- A `307` response in a test means the path is incorrect, i.e. missing a trailing `/`
- A `404` when expecting a difference response, such as a `422` for an invalid id, has an incorrect path, possibly from placing the `f` in an `f-string` inside the string instead of in front of it