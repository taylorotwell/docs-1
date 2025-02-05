# ⛔ Broadcast Rate Limiting

Rate limiting helps you throttle client events, backend events, or HTTP REST API calls for read endpoints (like `/channels`) at the [app](../app-management/introduction.md) level.

Choosing a rate limiter driver depends on the architecture the server is deployed in. For local, single-instance servers, the default local driver is sufficient. For multi-node deployments, a Redis server is typically required. If you choose to use Redis to store rate limiting data, please consult our documentation on [connecting to Redis](../getting-started/redis-configuration.md).

### Environment Variables

| Name                  | Default | Possible values  | Description                              |
| --------------------- | ------- | ---------------- | ---------------------------------------- |
| `RATE_LIMITER_DRIVER` | `local` | `local`, `redis` | The driver used for rate limiting. |

* `local` - Rate limiting data is stored in-memory and is lost upon server exit.
* `redis` - Rate limiting data is centralized in Redis. This driver is recommended when deploying multi-node soketi configurations.
