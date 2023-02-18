---
description: How to setup and configure the HTTP listener.
---

# HTTP Listeners

The VerneMQ HTTP listener is used to serve various VerneMQ subsystems such as:

* [Status page](../monitoring/status.md)
* [Prometheus metrics](../monitoring/prometheus.md)
* [management API](../live-administration/http-administration.md)
* [Health check](../monitoring/health-check.md)

By default it runs on port `8888`. To disable the HTTP listener or change the port, adapt the configuration in `vernemq.conf`:

```text
listener.http.default = 127.0.0.1:8888
```
It is possible to selectivly disable or enable the HTTP listeners of the various subsystems by setting the http_modules configuration setting. The following example  enables the status page on a seperate listener, the metrics and health apis on a second one, and the management api on a third one.

```text
listener.http.default = 127.0.0.1:8888
listener.http.default.http_modules = [vmq_metrics_http, vmq_health_http]
listener.http.status = 127.0.0.1:8888
listener.http.status.http_modules = [vmq_status_http]
listener.http.mgmt = 127.0.0.1:8888
listener.http.mgmt.http_modules = [vmq_http_mgmt_api]
```


