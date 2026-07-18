PYTHON ?= python3

.PHONY: up down logs install ingest ask psql clean

up:
	docker compose up -d
	@echo "Waiting for pgvector to be healthy..."
	@until [ "$$(docker inspect -f '{{.State.Health.Status}}' rag_pgvector_local 2>/dev/null)" = "healthy" ]; do sleep 1; done
	@echo "pgvector is up on port $${PGVECTOR_PORT:-5433}."

down:
	docker compose down

logs:
	docker compose logs -f

install:
	$(PYTHON) -m pip install -r requirements.txt

ingest:
	$(PYTHON) ingest.py

ask:
	$(PYTHON) rag.py "$(Q)"

psql:
	docker compose exec pgvector psql -U rag -d rag

clean:
	docker compose down -v
