# vuln2pve

<img src="img/vunl2pve.png" alt="Logo of vunl2pve" width="552" height="291">

[![Shellcheck on vuln2pve](https://github.com/53845714nF/vuln2pve/actions/workflows/lint_vuln2pve.yml/badge.svg)](https://github.com/53845714nF/vuln2pve/actions/workflows/lint_vuln2pve.yml)

## Berschreibung

vuln2pve ist ein kleines Shell Skript, was es erlaubt VMs von Vulnhub zu downloaden
und diese dann automatisiert auf Proxmox VE zu erstellen.
Es soll manuellen Arbeitsaufwand verringern. Daraus folgt, dass mit CTFs schneller begonnen werden kann. 😉

Ein ähnliches Projekt gab es unter: [ProxKube](https://github.com/Ap3x/ProxKube) \
Dieses wird leider nicht mehr weiterentwickelt.

## Installation von vuln2pve

Das vuln2pve Skript auf den Proxmox VE Host ablegen. Am besten im `/opt` oder `/usr/local/bin` Verzeichnis.

```bash
wget https://raw.githubusercontent.com/53845714nF/vuln2pve/main/vuln2pve -O /opt/vuln2pve && chmod u+x /opt/vuln2pve
```

## Verwendung

### Einstellungen für deine Umgebung

Standardwerte können ohne Bearbeitung des Skripts überschrieben werden, indem eine Konfigurationsdatei unter `~/.config/vuln2pve/vuln2pve.conf` angelegt wird:

Die folgenden Werte werden unterstützt:

| Wert            | Default              | Beschreibung                                      |
| --------------- | -------------------- | ------------------------------------------------- |
| `dns`           | `local`              | DNS-Nameserver für die VM                         |
| `storage`       | `local-lvm`          | Speicherort für die VM-Festplatte                 |
| `images_dir`    | `/var/lib/vz/images` | Proxmox images Verzeichnis                        |
| `bridge`        | `vmbr0`              | Netzwerk bridge                                   |
| `cores`         | `2`                  | Anzahl der CPU-Kerne                              |
| `memory`        | `1024`               | Arbeitsspeicher in MB                             |
| `keyboard`      | `de`                 | Tastaturbelegung                                  |
| `min_vm_id`     | `100`                | Mindest-VM-ID (einschließlich)                    |
| `max_vm_id`     | `0`                  | Maximale VM-ID (exklusiv), `0` = keine Begrenzung |

Beispielkonfiguration:

```toml
dns=1.1.1.1
bridge=vmbr1
memory=2048
min_vm_id=200
max_vm_id=300
```

### Command-line flags

Alle Konfigurationswerte können auch zur Laufzeit über Flags überschrieben werden, die Vorrang vor der Konfigurationsdatei haben:

```
  -b, --bridge      Network bridge
  -c, --cores       CPU cores
  -d, --dns         DNS nameserver
  -i, --images-dir  Images directory
  -k, --keyboard    Keyboard layout
  -m, --memory      Memory in MB
  -s, --storage     VM disk storage
      --min-id      Minimum VM ID (inclusive)
      --max-id      Maximum VM ID (exclusive), 0 = no limit
  -h, --help        Show help
```

### Download VM und konvertiert es zur Proxmox VM

```bash
./vuln2pve <url>
```

### Archive Konvertierung

Sucht im images Verzeichnis nach `.zip`, `.ova`, `.rar` oder `.vmdk` Dateien und konvertiert diese zur Proxmox VM

```bash
./vuln2pve
```

> [!WARNING]
> Die Dateien werden dabei gelöscht.

