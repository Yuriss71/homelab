# VM-001 : Bastion

## Informations générales

| Paramètre | Valeur |
|---|---|
| VM ID | 100 |
| Nom | bastion |
| OS | Ubuntu Server 24.04 LTS minimized |
| IP | 192.168.122.X |
| CPU | 2 cores |
| RAM | 1024 Mo |
| Disque | 20 Go |

## Rôle
Point d'entrée SSH unique de l'infrastructure.
Toutes les connexions vers les autres VMs passent par le bastion.
Personne ne se connecte directement aux autres VMs — on passe toujours par ici.

## Accès
```bash
ssh user@192.168.122.44
```

## Pourquoi un bastion ?
Au lieu d'exposer toutes les VMs directement, on centralise les accès
sur une seule machine. Si quelqu'un veut entrer dans l'infra, il doit
d'abord passer par le bastion. C'est plus simple à sécuriser, auditer,
et monitorer.

## Création dans Proxmox
- Create VM → General : nom `bastion`, VM ID `100`
- OS : ISO Ubuntu 24.04 LTS, Linux 6.x
- System : défaut
- Disks : local-lvm, 20 Go
- CPU : 2 cores
- Memory : 1024 Mo
- Network : vmbr0, VirtIO

## Notes
- Le disque de 20 Go est surdimensionné pour ce rôle.
  8-10 Go suffisent pour un bastion SSH. (panic)