# Scale workers

Workers are CPU-bound on PDF rendering and I/O-bound on webhooks.

## When to scale

- Queue lag over 2 minutes for 10 minutes
- Dead-letter growth with `timeout` errors
- PDF render time over 30 seconds

## How

```zsh
kubectl scale deploy/acme-worker --replicas=8
```

Scale API separately. Extra API replicas without workers make the queue worse.

## After a spike

Scale back once lag is under 30 seconds. Leave at least two replicas in `prod`.
