FROM python:3.13-slim

WORKDIR /app

RUN pip install --no-cache-dir uv

COPY pyproject.toml uv.lock .python-version ./
COPY ./src/titanic/api ./src/titanic/api

ENV UV_PROJECT_ENVIRONMENT=/tmp/kto-venv
ENV PATH="/tmp/kto-venv/bin:$PATH"

RUN uv sync -n --group api
RUN chmod -R a+rx /tmp/kto-venv

EXPOSE 8080

ENTRYPOINT ["python", "-m", "titanic.api"]