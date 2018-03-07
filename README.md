# Elasticsearch Cluster

Der Elasticsearch Cluster für mal eben schnell.

Die Konfiguration wurde ausgelagert, damit Language/Hyphenation Files benutzt werden können.

## Voraussetzungen
Der Elasticsearch-Cluster läuft auf einem Ubuntu 17.10
* mit docker und docker-compose

## Vorbereitung Linux für Elasticsearch

Vor dem Start von ES muss ein Kernelparameter angepasst werden.
```
sudo sysctl -w vm.max_map_count=262144
```

Für permanentes Setzen
```
$ grep vm.max_map_count /etc/sysctl.conf
vm.max_map_count=262144
```

Vor dem Start von Elasticsearch müssen Schreibrechte auf Verzeichnissen `es_cluster/data` und `es_cluster/config` mit
```
chmod a+x es_cluster/data
chmod a+x es_cluster/config

```
gegeben werden.

## Starten und Stoppen des Clusters
Der ES Cluster wird gestartet in Verzeichnis `/es_cluster/docker-compose` mit Kommando
```
sudo docker-compose up
```

Es wird ebenfalls ein Admintool für ES gestartet, `cerebro`, [localhost:9000](http://localhost:9000).
Für die Verbindung mit dem ES-Cluster wird eingegeben:  `http://esmaster:9200`


Gestoppt werden die Container mit CTRL-C. Wenn etwas ernsthaft hängenbleibt, kann man mit
```
sudo docker-compose rm
```
leicht beheben. Danach wieder mit `up` starten.
