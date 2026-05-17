# ADR-001 : Choix de l'hyperviseur

## Contexte
Besoin d'un hyperviseur pour faire tourner plusieurs VMs sur une seule
machine physique dans le cadre d'un homelab DevOps/Infrastructure.

## Options considérées

| Option | Points positifs | Points négatifs |
|---|---|---|
| VirtualBox | Simple, connu | Pas pro, limité, UI desktop |
| VMware Workstation | Stable, connu | Payant, pas orienté serveur |
| Proxmox VE | Gratuit, pro, UI web, clusters | Courbe d'apprentissage |

## Décision
**Proxmox VE** — hyperviseur bare-metal open source basé sur Debian.
Accessible via interface web, supporte KVM (VMs) et LXC (containers),
utilisé en production dans de nombreuses entreprises.

## Conséquences
- ✅ Interface web accessible depuis n'importe quelle machine du réseau
- ✅ Stack 100% open source et gratuite
- ✅ Correspond aux standards du marché DevOps/Infra
- ⚠️ Nécessite d'être installé en bare-metal (remplace l'OS principal)