# 🏗️ Homelab Infrastructure Portfolio

Infra complète montée de zéro à des fins d'apprentissage DevOps/Infrastructure.
Chaque composant est documenté, chaque choix technique est justifié.

## 🎯 Objectifs

- Monter une infrastructure réelle de bout en bout
- Couvrir toutes les couches : réseau, virtualisation, containers, orchestration, CI/CD, observabilité, sécurité
- Documenter chaque étape pour en faire un portfolio technique

## 🗺️ Architecture globale

> Schéma à venir — voir `docs/architecture/NETWORK.md`

## 📦 Stack technique

| Couche | Technologies |
|---|---|
| Hyperviseur | Proxmox VE |
| Réseau | pfSense, VLANs, DNS local |
| IaC | Terraform, Ansible |
| Containers | Docker, Docker Compose |
| Orchestration | Kubernetes (k3s) |
| CI/CD | GitHub Actions, ArgoCD |
| Observabilité | Prometheus, Grafana, Loki |
| Sécurité | Vault, Trivy, cert-manager |
       

## 📊 Avancement

| Phase | Contenu | Statut |
|---|---|---|
| Phase 1 | Réseau, Proxmox, VMs socle | 🔄 En cours |
| Phase 2 | Docker, Ansible | ⏳ À venir |
| Phase 3 | Kubernetes (k3s) | ⏳ À venir |
| Phase 4 | CI/CD | ⏳ À venir |
| Phase 5 | Observabilité | ⏳ À venir |
| Phase 6 | Sécurité | ⏳ À venir |