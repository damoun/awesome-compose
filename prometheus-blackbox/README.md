# Prometheus / Blackbox Exporter

## Quick start

```bash
$ docker compose up
[+] Running 3/3
 ✔ Network prometheus-blackbox_default  Created   0.0s
 ✔ Container blackbox_exporter          Started   0.0s
 ✔ Container prometheus                 Started   0.0s
```

## Expected result

Listing containers must show two containers running and the port mapping as below:

```bash
$ docker ps
CONTAINER ID   IMAGE                                  COMMAND                  CREATED         STATUS         PORTS                    NAMES
0706069b700e   quay.io/prometheus/prometheus          "/bin/prometheus --c…"   2 seconds ago   Up 2 seconds   0.0.0.0:9090->9090/tcp   prometheus
4b4039aea377   quay.io/prometheus/blackbox-exporter   "/bin/blackbox_expor…"   2 seconds ago   Up 2 seconds   0.0.0.0:9115->9115/tcp   blackbox_exporter
```

Navigate to [http://localhost:9090](http://localhost:9090) in your web browser to access Prometheus or [http://localhost:9115](http://localhost:9115) to access Blackbox Exporter.

## Cleanup

Stop and remove the containers. Use -v to remove the volumes if looking to erase all data.

```bash
$ docker compose down -v
```
