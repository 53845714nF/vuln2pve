# vuln2pve

<img src="img/vunl2pve.png" alt="Logo of vunl2pve" width="552" height="291">

[![Shellcheck on vuln2pve](https://github.com/53845714nF/vuln2pve/actions/workflows/lint_vuln2pve.yml/badge.svg)](https://github.com/53845714nF/vuln2pve/actions/workflows/lint_vuln2pve.yml)

English version below

## Berschreibung

vuln2pve ist ein kleines Shell Skript, was es erlaubt VMs von Vulnhub zu downloaden
und diese dann automatisiert auf Proxmox VE zu erstellen.
Es soll manuellen Arbeitsaufwand verringern. Daraus folgt, dass mit CTFs schneller begonnen werden kann. 😉

Ein ähnliches Projekt gibt es unter: [ProxKube](https://github.com/Ap3x/ProxKube) \
Dieses bietet zwar mehr Möglichkeiten, braucht aber dafür mehr Nutzerinteraktion.

## Installation von vuln2pve

Das vuln2pve Skript auf den Proxmox VE Host ablegen. Am besten im `/opt` oder `/usr/local/bin` Verzeichnis.

```bash
wget https://raw.githubusercontent.com/53845714nF/vuln2pve/main/vuln2pve -O /opt/vuln2pve && chmod u+x /opt/vuln2pve
```

## Verwendung

### Einstellungen für deine Umgebung

```bash
# Please adapt for your environment 
dns=local # like fritz.box
storage=vm_pool # default is local-lvm
images_dir=/var/lib/vz/images # default pve dir
```

### Download VM und konvertiert es zur Proxmox VM

```bash
./vuln2pve <url>
```

### Sucht im images Verzeichnis nach `.zip`, `.ova`, `.rar` oder `.vmdk` Dateien und konvertiert diese zur Proxmox VM

```bash
./vuln2pve
```

> [!WARNING]
> Die Dateien werden dabei gelöscht.

---

## Description

vuln2pve is a small Shell Script that downloads VM's from Vulnhub and converts them to the Proxmox VE format.
Helpful to avoid manual steps so you can start quickly with your CTF's. 😉

There is a similar project at: [ProxKube](https://github.com/Ap3x/ProxKube) \
This offers more features but requires more user interaction.

## Installation of vuln2pve

Copy the vuln2pve file to your Proxmox VE Host. Recommended location is either the `/opt` or `/usr/local/bin` directory.

```bash
wget https://raw.githubusercontent.com/53845714nF/vuln2pve/main/vuln2pve -O /opt/vuln2pve && chmod u+x /opt/vuln2pve
```

## Usage

### Configuration file

Defaults can be overridden without editing the script by creating a config file at:

```
~/.config/vuln2pve/vuln2pve.conf
```

The following variables are supported:

| Variable | Default | Description |
|---|---|---|
| `dns` | `local` | DNS nameserver for the VM |
| `storage` | `local-lvm` | Storage location for the VM disk |
| `images_dir` | `/var/lib/vz/images` | Proxmox images directory |
| `bridge` | `vmbr0` | Network bridge |
| `cores` | `2` | Number of CPU cores |
| `memory` | `1024` | Memory in MB |
| `keyboard` | `de` | Keyboard layout |
| `min_vm_id` | `100` | Minimum VM ID (inclusive) |
| `max_vm_id` | `0` | Maximum VM ID (exclusive), `0` = no limit |

Example config:

```bash
dns=1.1.1.1
bridge=vmbr1
memory=2048
min_vm_id=200
max_vm_id=300
```

### Command-line flags

All config values can also be overridden at runtime via flags, which take precedence over the config file:

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

### Download a VM and convert it to Proxmox VE format:

```bash
./vuln2pve <url>
```

### Searches the images directory (`images_dir`) for `.zip`, `.7z`, `.ova`, `.rar`, `.vdi` or `.vmdk` files and converts them to Proxmox VE format:

```bash
./vuln2pve
```

> [!WARNING]
> The files will be deleted.
