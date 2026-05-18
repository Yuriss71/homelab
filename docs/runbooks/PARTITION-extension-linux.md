# Runbook : Extension de la partition Linux en dual boot

## Contexte
Machine en dual boot Windows/Linux sur un seul NVMe.
Objectif : donner plus d'espace à Linux sans casser le dual boot.

## Prérequis
- Une clé USB (8 Go minimum)
- Ventoy installé sur la clé
- ISO GParted Live

## Étapes

### 1. Réduire la partition Windows
- Ouvrir `diskmgmt.msc` sur Windows
- Clic droit sur `C:` → Réduire le volume
- Entrer la quantité en Mo (ex: 153600 = 150 Go)
- Valider → un espace non alloué apparaît

### 2. Préparer la clé USB bootable
- Installer Ventoy sur la clé :
  `sudo ./Ventoy2Disk.sh -i /dev/sdX`
- Copier l'ISO GParted sur la partition Ventoy :
  `sudo cp gparted-live-*.iso /mnt/`

### 3. Étendre la partition Linux avec GParted
- Booter sur la clé USB (F12 au démarrage sur Gigabyte)
- Sélectionner l'ISO GParted dans Ventoy
- Dans GParted : clic droit sur la partition Linux → Resize/Move
- Étendre jusqu'à prendre tout l'espace non alloué
- Appliquer les changements

## Résultat
Partition Linux étendue de 117 Go à 267 Go sans toucher au dual boot.

## Outils utilisés
- `diskmgmt.msc` — gestionnaire de partitions Windows
- Ventoy — outil de clé USB multi-ISO
- GParted Live — éditeur de partitions graphique