FROM python:3.12-slim

# Install uv.
COPY --from=ghcr.io/astral-sh/uv:latest /uv /uvx /bin/

WORKDIR /app

EXPOSE 8000

# Copy requirements and install dependencies
COPY pyproject.toml  uv.lock ./
RUN uv sync --frozen --no-cache

# Copy application code
COPY . /app/

# Set environment variables
ENV PYTHONPATH=/app

# Command to run the application
CMD ["uv", "run", "uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
