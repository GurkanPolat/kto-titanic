FROM python:3.13-slim

WORKDIR /app

ENV PYTHONPATH=/app/src

RUN pip install --no-cache-dir uv

COPY pyproject.toml uv.lock .python-version ./
COPY ./src ./src

ENV UV_PROJECT_ENVIRONMENT=/tmp/kto-venv
ENV PATH="/tmp/kto-venv/bin:$PATH"

RUN uv sync -n --group api
RUN chmod -R a+rx /tmp/kto-venv

EXPOSE 8080

ENTRYPOINT ["api"]