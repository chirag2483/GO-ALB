# GO-ALB

`GO-ALB` is a lightweight HTTP load balancer written in Go.

It routes incoming traffic to backend servers and supports two balancing strategies:
- Round Robin
- Least Connections

## Project Structure

- `main.go`: entrypoint and server setup
- `backend/`: backend instance behavior and liveness helpers
- `frontend/`: request forwarding layer
- `serverpool/`: balancing strategy and pool management
- `utils/`: shared utility helpers
- `config.yaml`: runtime configuration

## Configuration

The balancer reads settings from `config.yaml`.

Example:

```yaml
lb_port: 3333
strategy: least-connection
retry_limit: 3
backends:
  - "http://localhost:100"
  - "http://localhost:101"
```

Fields:
- `lb_port`: port exposed by the load balancer
- `strategy`: `round-robin` (default) or `least-connection`
- `retry_limit`: retry attempts before marking backend unavailable
- `backends`: list of backend URLs

## Run

```bash
go run .
```

## Test

```bash
go test ./...
```
