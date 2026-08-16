# RHEL 10 Hardening for AWX

Projet Ansible de hardening RHEL 10 conçu pour être exécuté depuis AWX.

## Modes

- `hardening_mode=audit` : contrôle sans modification.
- `hardening_mode=enforce` : applique les remédiations.
- `hardening_mode=rollback` : restaure les fichiers sauvegardés par les rôles qui le permettent.

## Exemple AWX

1. Créer un Project pointant vers ce dépôt.
2. Créer un Inventory contenant les hôtes RHEL 10.
3. Créer un Job Template `RHEL10 - Hardening - Audit` avec `playbooks/audit.yml`.
4. Créer un Job Template `RHEL10 - Hardening - Enforce` avec `playbooks/hardening.yml`.
5. Exposer les variables du fichier `group_vars/all/main.yml` via Survey si nécessaire.
6. Tester d'abord sur DEV puis QUALIF/PROD.

## Attention

Cette base est volontairement conservatrice. Les valeurs doivent être validées contre le benchmark CIS RHEL 10 applicable à votre environnement avant production.
Les contrôles liés à PAM, SSH, firewall, crypto-policy et partitions peuvent provoquer une perte d'accès ou une incompatibilité applicative s'ils sont appliqués sans validation.
