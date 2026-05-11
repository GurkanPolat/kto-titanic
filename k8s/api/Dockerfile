FROM python:3.13-slim

WORKDIR /app

ENV PYTHONPATH=/app/src

RUN pip install --no-cache-dir uv

COPY pyproject.toml uv.lock .python-version ./
COPY ./src ./src

RUN uv pip install --system --group api .

EXPOSE 8080

ENTRYPOINT ["python", "-m", "titanic.api.main"]