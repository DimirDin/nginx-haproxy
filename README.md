# Домашнее задание: Кластеризация и балансировка нагрузки

**Студент:** Гридин Владимир

---

## Задание 1: Round-robin на 4 уровне

### HAProxy config

```cfg
global
    daemon
    maxconn 256

defaults
    mode tcp
    timeout connect 5000ms
    timeout client 50000ms
    timeout server 50000ms

frontend web_frontend
    bind *:80
    default_backend web_servers

backend web_servers
    balance roundrobin
    server s1 127.0.0.1:8888 check
    server s2 127.0.0.1:9999 check
```

![Задание 1](img/1.png)

## Задание 2: Weighted Round Robin на 7 уровне

- Домен: `example.local`
- `curl http://example.local` — чаще Server 3, затем 2, затем 1
- `curl http://localhost` — 503 ошибка

![Задание 2](img/2.png)
---