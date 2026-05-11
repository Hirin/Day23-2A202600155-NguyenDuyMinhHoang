# BONUS B1: eBPF Profiling with Pyroscope (+10 pts)

## Setup

Already integrated into `docker-compose.yml` as the `pyroscope` service.

The FastAPI app (`01-instrument-fastapi/app/instrumentation.py`) auto-connects to Pyroscope via `PYROSCOPE_SERVER_ADDRESS` env var.

## Run

```bash
make up          # starts pyroscope alongside the core stack
make load        # generate traffic
```

## View Flame Graph

1. Open http://localhost:4040
2. Select application **day23-app**
3. You will see a flame graph of the Python process
4. Screenshot this for the rubric checkpoint

## What to screenshot

- Pyroscope UI showing the **day23-app** flame graph with function-level profiling data
