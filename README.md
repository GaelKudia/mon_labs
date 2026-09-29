# 🛡️ SOC Home Lab - Gael Kudia | DevSecOps & Blue Team

> Administrateur Système & Sécurité Opérationnelle | M1 Informatique - ULK | Kinshasa, RDC

Laboratoire virtuel complet simulant une infrastructure d'entreprise sécurisée, de type PME / Imprimerie.

## 🏗️ Architecture

**Segmentation réseau :** WAN / LAN / DMZ gérée par pfSense
**Red Team :** Kali Linux pour scans, injections
**Blue Team :** Ubuntu Server durci

## 📦 Projets Documentés

### 1. Projet Dispromalt - Déploiement Sécurisé [PROD]
- **Rapports :** `Rapport_Deploiement_Dispromalt.pdf`
- Hardening : UFW, OpenSSH (port 22), `ssh-keygen -t ed25519`, VirtualHost Apache isolé (DocumentRoot /public, mod_rewrite, FallbackResource)
- BDD : `GRANT ALL PRIVILEGES ON dispro_db.* TO symfony_user@localhost`
- Debug : `doctrine:schema:update --force`, `cache:clear --env=prod`

### 2. Stack de Monitoring & Observabilité [DevSecOps]
- **Rapports :** `Briefing_des_réalisations_du_jour.docx`
- **Stack :** `compose.monitoring.yaml` -> prom/prometheus:v2.45.0 + prom/node-exporter:v1.6.1 + grafana/grafana:10.0.0
- **Incident résolu :** `No data` sur Grafana ID 1860 causé par incompatibilité cAdvisor v0.47+ avec cgroups v2 Ubuntu 24.04. Migration vers Node Exporter.
- **Config :** scrape_interval 15s, volume persistant grafana-data, restart: unless-stopped

### 3. SOC / SIEM - Wazuh
- Collecte centralisée de `/var/log/apache2/disproamlt_access.log` (format combined)
- Parsing Bash pattern "admin"
- Endpoint : Kaspersky centralisé + Honeypots pour Threat Intelligence
- Analyse réseau : Wireshark

## 🛠️ Compétences Validées
`Linux` `Bash` `pfSense` `UFW` `Apache2` `Docker Compose` `Prometheus` `Grafana` `Wazuh` `Wireshark` `Git SSH Ed25519` `Symfony` `Doctrine`

## 🔜 Next Steps
- [ ] CI/CD Pipeline : Trivy scan + gitleaks
- [ ] Attaque Kali -> Détection Wazuh -> Dashboard Grafana
- [ ] Rapport MITRE ATT&CK

---
**Contact :** linkedin.com/in/gael-kudia
