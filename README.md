# Grafana Monitor

Install the [Loki Driver](https://grafana.com/docs/loki/latest/clients/docker-driver/) first.

And then in the `docker-compose.yml` file: 

```yml
version: '3.7'

services:
  grafana:
    image: grafana/grafana-oss
    ports:
      - 3000:3000
    volumes:
      - grafana-storage:/var/lib/grafana

  loki:
    image: grafana/loki
    ports:
      - "3100:3100"
    command: -config.file=/etc/loki/local-config.yaml
    volumes:
      - loki-storage:/var/lib/loki
```

Finally just simply run:
```shell
$ docker compose up -d
```
and you can see the grafana client live on `localhost:3000`.