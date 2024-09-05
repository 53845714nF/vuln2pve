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

vuln2pve is a small Shell Script, it try to download VM's from Vulnhub and convert this to the Proxmox VE format.
Should avoid manual steps so you can start quickly with your CTF's. 😉

There is a similar project at: [ProxKube](https://github.com/Ap3x/ProxKube) \
This offers more features but requires more user interaction.

## Installation of vuln2pve

Copy the vuln2pve file to your Proxmox VE Host the best in the `/opt` or `/usr/local/bin` Directory.

```bash
wget https://raw.githubusercontent.com/53845714nF/vuln2pve/main/vuln2pve -O /opt/vuln2pve && chmod u+x /opt/vuln2pve
```

## Usage

### Setup for your environment

```bash
# Please adapt for your environment 
dns=local # like fritz.box
storage=vm_pool # default is local-lvm
images_dir=/var/lib/vz/images # default pve dir
```

### Download VM and try to convert

```bash
./vuln2pve <url>
```

### Lock in the images Directory and search for `.zip`, `.ova`, `.rar` or `.vmdk` files and convert them to Proxmox VM's

```bash
./vuln2pve
```

> [!WARNING]
> The files will be deleted.
