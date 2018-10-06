# Routerkonfiguration

[![Build Status](https://travis-ci.com/Technik-AG/router-configuration.svg?branch=master)](https://travis-ci.com/Technik-AG/router-configuration)

Dieses paket enthält alle notwendigen Konfigurationsdateien, um auf dem Ethernet-Port eine Internetfreigabe einzurichten.

## Funktionsweise

Es wird mithilfe von NetworkManager eine Verbindung auf dem Ethernet-Port namens `Technik-AG shared ethernet` erstellt.
NetworkManager richtet dadurch folgendes automatisch ein:

* Weiterleitung der Pakete vom Ethernet-Port auf die aktive Internet-Schnittstelle
* NAT auf der Internet-Schnittstelle
* Einen DHCP- und DNS-Server auf dem Ethernet-Port mithilfe von `dnsmasq-base`

Die Verbindung hat eine Priorität von `1` und sollte damit automatisch aktiviert werden (Der Standard ist `0`).

## Konfiguration des DHCP- und DNS-Servers

Der DHCP- und DNS-Server kann mithilfe von Dateien im Ordner `/etc/NetworkManager/dnsmasq-shared.d` konfiguriert werden.
Beispiele für mögliche Konfigurationsoptionen können in [`dnsmasq.conf.example`](http://thekelleys.org.uk/gitweb/?p=dnsmasq.git;a=blob;f=dnsmasq.conf.example;hb=refs/heads/master) in der Repository von dnsmasq gefunden werden.

## Erstellen des Pakets

Folgendes Kommando erstellt das Paket im Ordner `build/distributions`:

```shell
./gradlew build
```

Unter Windows muss entweder PowerShell benutzt oder `./` weggelassen werden.