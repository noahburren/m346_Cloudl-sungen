# Kostenvergleich und Bewertung von Cloud-Migrationsstrategien

Dieses Dokument enthält eine Übersicht der Kosten für die verschiedenen Migrationsstrategien (IAAS, PAAS, SAAS) und deren Vorteile.

---

## A) Kostenrechnung IAAS - Rehosting

### Amazon Web Services (AWS)
#### Webserver
- **Service:** Amazon EC2
- **Betriebssystem:** Ubuntu Pro
- **Instanztyp:** t3.small (2 vCPUs, 2 GiB RAM, EBS only)
- **Reservierungslaufzeit:** 3 Jahre
- **Kosten:** 12.99 €/Monat

#### Datenbank
- **Service:** Amazon RDS
- **Instanztyp:** db.t3.medium (2 vCPUs, 4 GiB RAM, 100 GB Storage)
- **Kosten:** 193.99 €/Monat

#### Backup
- **Service:** Amazon S3
  - Datenübertragungskosten: 3.15 €/Monat
  - S3 Standard: 28.33 €/Monat
  - S3 Glacier Deep Archive: 3.72 €/Monat
- **Gesamtkosten:** 35.20 €/Monat

---

### Microsoft Azure
#### Webserver
- **Service:** B1ms
- **Betriebssystem:** Ubuntu
- **Spezifikationen:** 1 Core, 2 GB RAM, 4 GB Temporary Storage
- **Disk:** S4 32 GiB
- **Savings Plan:** 3 Jahre (~45 % Rabatt)
- **Kosten:** 12.29 €/Monat

#### Datenbank
- **Service:** Azure SQL Database
  - Typ: Single Database, vCore, General Purpose
  - Spezifikationen: 2 vCore, 100 GB Storage, 4 GB RAM
  - Savings Plan: 3 Jahre reserved
  - SQL-Lizenz: Azure Hybrid Benefit
- **Kosten:** 143.37 €/Monat

#### Backup
- **Service:** Block Blob Storage
  - Hot Storage: 20.80 €/Monat
  - Cool Storage: 15.20 €/Monat
  - Cold Storage: 3.60 €/Monat
- **Gesamtkosten:** 39.60 €/Monat

---

## B) Kostenrechnung PAAS - Replattforming
- **Details:** Siehe Bilder (Heroku_(1,2,3))

---

## C) Kostenrechnung SAAS - Repurchasing

### Auswahlmöglichkeiten
1. **Zoho CRM**
   - **Plan:** Professional Plan
   - **Kosten:** 23 €/User/Monat * 30 User = 690 €/Monat

2. **Salesforce**
   - **Plan:** Starter Suite
   - **Kosten:** 25 €/User/Monat * 30 User = 750 €/Monat

### Ausgewählte Lösung: **Zoho CRM**
- **Begründung:**
  - Günstiger (690 € vs. 750 €)
  - Bietet mehr Funktionen als Salesforce Starter Suite (z. B. Automatisierungen)
  - Einfachere Implementierung
  - Bessere Anpassungsoptionen

---

## Fazit
Diese Kostenübersicht dient als Grundlage zur Auswahl der besten Strategie für die Cloud-Migration basierend auf spezifischen Anforderungen und Budget.
