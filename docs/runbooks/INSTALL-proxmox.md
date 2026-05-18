# Runbook : Installation Proxmox VE dans KVM

## Contexte
Proxmox VE installé dans une VM KVM sur Linux (contrainte dual boot).
Machine hôte : Ubuntu, AMD Ryzen, 16 Go RAM, KVM activé.

## Prérequis
- KVM/QEMU installé sur la machine hôte
- ISO Proxmox VE téléchargée dans `/var/lib/libvirt/images/`
- Virtualisation imbriquée activée

## Étapes

### 1. Activer la virtualisation imbriquée (AMD)
```bash
sudo modprobe -r kvm_amd
sudo modprobe kvm_amd nested=1
echo "options kvm_amd nested=1" | sudo tee /etc/modprobe.d/kvm-amd.conf
cat /sys/module/kvm_amd/parameters/nested
```

### 2. Créer la VM Proxmox
```bash
sudo virt-install \
  --name proxmox \
  --ram 8192 \
  --vcpus 4 \
  --cpu host-passthrough \
  --disk path=/var/lib/libvirt/images/proxmox.qcow2,size=100 \
  --cdrom /var/lib/libvirt/images/proxmox-ve_9.1-1.iso \
  --os-variant debian12 \
  --network network=default \
  --graphics vnc \
  --noautoconsole
```

### 3. Suivre l'installation via virt-manager
```bash
sudo virt-manager &
```
- Double-cliquer sur la VM `proxmox`
- Sélectionner **Install Proxmox VE (Graphical)**
- Disque cible : `/dev/vda (100 GiB)`
- Hostname : `pve.homelab.local`
- IP : `192.168.122.17/24`
- Gateway + DNS : `192.168.122.1`

### 4. Accéder à l'interface web
https://192.168.122.17:8006
Login : `root` / mot de passe défini pendant l'install.

## Résultat
Proxmox VE 9.1 opérationnel, accessible via navigateur depuis la machine hôte.