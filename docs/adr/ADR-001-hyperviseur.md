# ADR-001 : Choix de l'hyperviseur

## Contexte
Besoin d'un hyperviseur pour faire tourner plusieurs VMs sur une seule
machine physique dans le cadre d'un homelab DevOps/Infrastructure.
Contrainte : machine principale en dual boot Windows/Linux, impossible
d'installer Proxmox en bare-metal sans perdre le dual boot.

## Options considérées

| Option | Points positifs | Points négatifs |
|---|---|---|
| VirtualBox | Simple, connu | Pas pro, limité, UI desktop |
| VMware Workstation | Stable, connu | Payant, pas orienté serveur |
| Proxmox VE bare-metal | Gratuit, pro, UI web | Casse le dual boot |
| Proxmox VE dans KVM | Garde le dual boot, même logique | Performances réduites |

## Décision
**Proxmox VE dans une VM KVM** via VirtualBox/VMware sur Linux.
Même stack technique, même apprentissage, sans sacrifier le dual boot.
Migration vers bare-metal possible plus tard sur machine dédiée.

## Conséquences
- ✅ Dual boot Windows/Linux préservé
- ✅ Stack 100% identique à un vrai déploiement
- ✅ Facilement migrable vers bare-metal
- ⚠️ Performances légèrement réduites (virtualisation imbriquée)