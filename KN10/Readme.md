# Kostenvergleich und Bewertung von Cloud-Migrationsstrategien

Herr Atilgan,
dieses Dokument bietet eine Übersicht zu den Kosten und dem Aufwand der Cloud-Migrationsstrategien (IaaS, PaaS, SaaS) sowie meine Bewertung zu den Optionen basierend auf unseren bisherigen Anforderungen.

---

## Kostenvergleich

### Infrastructure-as-a-Service (IaaS)
#### Amazon Web Services (AWS)
- **Webserver**: 12,99 €/Monat
![Webserver](Kostenberechnung_Webserver_AWS.png)
- **Datenbank**: 193,99 €/Monat
![Datenbank](Kostenberechnung_Datenbank_AWS.png)
- **Backup**: 35,20 €/Monat
![Backup_1](Kostenberechnung_Backup_AWS_1.png)
![Backup_2](Kostenberechnung_Backup_AWS_2.png)
![Backup_3](Kostenberechnung_Backup_AWS_3.png)
- **Gesamtkosten**: 242,18 €/Monat

#### Microsoft Azure
- **Webserver**: 12,29 €/Monat
![Webserver_1](Kostenberechnung_Webserver_Azure_1.png)
![Webserver_2](Kostenberechnung_Webserver_Azure_2.png)
- **Datenbank**: 143,37 €/Monat
![Datenbank_1](Kostenberechnung_Webserver_Azure_1.png)
![Datenbank_2](Kostenberechnung_Webserver_Azure_2.png)
- **Backup**: 39,60 €/Monat
![Backup](Kostenberechnung_Backup_Azure.png)
- **Gesamtkosten**: 195,26 €/Monat

### Platform-as-a-Service (PaaS)
- **Heroku**:
- Production wurde gewählt, da es für unserere Lösung reicht und die Kosten am geringsten sind. Kosten: 50 €/Monat
![Heroku_1](Heroku_1.png)
- Hier wurde die Standard-Option gewählt, da es mit unseren Anforderungen übereinstimmt, skalierbar ist und der Preis am geringsten ist. Für 30 Benutzer ist das ausreichend. Kosten: 50 €/Monat
![Heroku_2](Heroku_2.png)
- Auch hier wurde die Standard-Version gewählt, da sie für unsere Lösung ausreicht. Backups sind im Plan enthalten.
![Heroku_3](Heroku_3.png)
- Bei Bedarf kann man den Logging/Monitoring-Zusatzdienst hinzufügen, falls Sie Protokolle und Fehlerverfolgungen möchten. Das wären dann nochmal 10 €/Monat.
- **Gesamtkosten**: 110 €/Monat

### Software-as-a-Service (SaaS)
#### Zoho CRM
- **Kosten**: 690 €/Monat (23 €/User für 30 User)
![ZohoCRM](ZohoCRM_Auswahlmöglichkeiten.png)
- Empfohlener Plan: Professional
- Bietet alle wichtigen CRM-Funktionen, mit einbeschlossen Automatisierungen.
- Gute Balance zwischen Kosten und Funktionen

#### Salesforce
- **Kosten**: 750 €/Monat (25 €/User für 30 User)
![SalesForce](SalesForce_Auswahlmöglichkeiten.png)
- Empfohlener Plan: Starter Suite
- Grundlegende CRM-Funktionen sind enthalten, welche unseren Anforderungen entsprechen.
- Kostengünstigste Option

---

## Erklärung zur Auswahl der Cloud-Komponenten und Abweichungen zur bisherigen On-Premise-Infrastruktur

### 1. Webserver
#### On-Premise Infrastruktur:
- 1 Core, 2 GB RAM, 20 GB Speicher, Ubuntu.
- Der Webserver ist einfach konfiguriert und dient eigentlich nur zur Bereitstellung der Anwendung.

#### Cloud-Komponente:
- **AWS**: Amazon EC2 (t3.small: 2 vCPUs, 2 GiB RAM, Reservierungslaufzeit 3 Jahre).
- **Azure**: Virtual Machine (B1ms: 1 vCPU, 2 GB RAM, 4 GB Temporary Storage, S4 32 GiB, Saving Plan 3 Jahre (~45% Rabatt)).

#### Abweichungen und Gründe:
- Die kleinsten verfügbaren Instanzen in der Cloud sind meistens leistungsstärker und bieten mehr Ressourcen (z. B. 2 vCPUs bei AWS).
- Die Speichergröße (20 GB) wird durch die Festplattenoption bereitgestellt.
- **Gründe**:
  - Die Wahl fiel auf die günstigsten Instanzen, die den Anforderungen entsprechen.
  - Vorteil: Skalierbarkeit. Bei Bedarf können die Ressourcen schnell angepasst werden.
  - Grund für Abweichung: Cloud-Instanzen sind vorab definiert, daher keine 1:1 Anpassung möglich.

### 2. Datenbankserver
#### On-Premise Infrastruktur:
- 2 Cores, 4 GB RAM, 100 GB Speicher, Ubuntu.
- Datenbankserver wurde manuell verwaltet.

#### Cloud-Komponente:
- **AWS**: Amazon RDS (db.t3.medium: 2 vCPUs, 4 GiB RAM, 100 GB Storage).
- **Azure**: Azure SQL Database (General Purpose, 2 vCores, 4 GB RAM, 100 GB Speicher, Savings Plan 3 Years reserved, Azure Hybrid Benefit SQL-Licence).

#### Abweichungen und Gründe:
- **Managed Service**:
  - Statt einer selbst verwalteten VM wurde ein Managed Database Service gewählt.
  - Vorteil: Automatisierte Backups und Upgrades.
  - Grund für Abweichung: Der Betrieb eines Managed Service reduziert den administrativen Aufwand und die Fehlerquellen.
- **Speichergröße**:
  - Die Spezifikationen (100 GB) wurden übernommen, mit der Möglichkeit, sie bei Bedarf zu skalieren.
- **Performance**:
  - RDS und Azure SQL bieten eine optimierte Umgebung für Datenbanken (natürlich besser als eine manuelle Installation auf einer VM).

### 3. Backups
#### On-Premise Infrastruktur:
- Manuelle Speicherung der Backups auf lokalem Speicher.
- **Backup-Plan:**
  - Täglich für die letzten 7 Tage.
  - Wöchentlich für den letzten Monat.
  - Monatlich für die letzten 3 Monate.

#### Cloud-Komponente:
- **AWS**:
  - Tägliche Backups: Amazon S3 Standard.
  - Wöchentliche Backups: Amazon S3 Infrequent Access.
  - Monatliche Backups: Amazon S3 Glacier (bzw. Deep Archive).
- **Azure**:
  - Tägliche Backups: Blob Storage Hot Tier.
  - Wöchentliche Backups: Blob Storage Cool Tier.
  - Monatliche Backups: Blob Storage Archive Tier.

#### Abweichungen und Gründe:
- **Kosteneffizienz**:
  - Statt eines einheitlichen Speichers (wie bei On-Premise) wurde eine abgestufte Speicherlösung gewählt.
  - Cool Backups sind günstiger als heiße Speicheroptionen.
- **Zugriffszeiten**:
  - Tägliche Backups bleiben schnell verfügbar (Hot).
  - Wöchentliche/monatliche Backups werden seltener benötigt und können daher in günstigeren Stufen gespeichert werden (Cool/Archive).
- **Sicherheit und Redundanz**:
  - Cloud-Backups werden in verteilten Regionen gespeichert, was bei On-Premise nicht möglich ist.

---

## Aufwand für die Firma

### AWS, Azure (IaaS)
- Höherer technischer Aufwand für uns (z. B. Einrichtung, Datenmigration, Verwaltung).

### Heroku (PaaS)
- Reduzierter Verwaltungsaufwand durch automatisierte Plattformdienste.
- Anpassungen wären möglich, aber wir haben nur eingeschränkte Kontrolle.

### Zoho CRM, Salesforce (SaaS)
- Minimaler technischer Aufwand.
- Der Fokus liegt auf Schulung und der Workflow-Integration.

### Erklärung der Unterschiede im Aufwand
1. **Technische Anforderungen:**
   - **AWS, Azure:** Höherer technischer Aufwand, da die gesamte Infrastruktur manuell auf die Cloud migriert werden muss. Anpassungen und fortlaufende Wartung bleiben Aufgabe von uns.
   - **Heroku:** Reduziert den Aufwand durch vorgefertigte Plattformdienste, erfordert jedoch Anpassungen an bisher bestehende Anwendungen.
   - **Zoho CRM und Salesforce:** Minimiert den technischen Aufwand, da die Infrastruktur vollständig von den Anbietern verwaltet wird.

2. **Schulung und Einarbeitung:**
   - Zoho CRM und Salesforce erfordern eine Einarbeitung der Mitarbeiter in neue Workflows und Funktionen.  
   - AWS und Azure benötigen keine Endbenutzerschulung, erfordern jedoch mehr Aufwand für unsere IT-Abteilung.

3. **Langfristige Wartung:**
   - **AWS, Azure und Heroku:** Die Firma trägt weiterhin die Verantwortung für Updates, Sicherheit und Optimierungen.
   - **Zoho CRM und Salesforce:** Updates und Wartung werden vollständig vom Anbieter übernommen.

---

## Vergleich nach Kosten

- **AWS (Rehosting)**: 242,18 €/Monat
- **Azure (Rehosting)**: 195,26 €/Monat
- **Heroku (Replatforming)**: 110€/Monat
- **Zoho CRM (SaaS)**: 690€/Monat
- **Salesforce (SaaS)**: 750€/Monat

### Warum sind die Kosten unterschiedlich?
1. **Flexibilität vs. Fertige Lösung:**
   - **AWS, Azure, Heroku:** Man zahlt nur für die genutzte Infrastruktur. Diese Lösungen erfordern zusätzliche Arbeit für Anpassungen, Verwaltung und Wartung, was die Kosten sinkt, aber langfristige Betriebskosten hinzufügt.
   - **Zoho, Salesforce:** SaaS-Lösungen beinhalten fertige Funktionen und minimale Administrationsarbeit, was die Grundkosten erhöht, jedoch den Aufwand für uns reduziert.

2. **Angebot und Spezialisierung:**
   - **AWS und Azure** bieten nahezu identische Infrastrukturkomponenten. Unterschiede in den Kosten kommen durch die Preisgestaltung, die Support-Optionen und sdie pezifischen Dienste zustande.
   - **Heroku** bietet eine benutzerfreundliche Entwicklerplattform, was unseren Aufwand reduziert, jedoch teurer ist als reine Cloud-Dienste.
   - **Zoho CRM und Salesforce** bieten hochspezialisierte CRM-Funktionen. Salesforce verlangt höhere Preise, bietet aber mehr Anpassungsmöglichkeiten.

3. **Skalierung und Zusatzdienste:**
   - AWS und Azure bieten größere Flexibilität und Skalierbarkeit, haben jedoch dann zusätzliche Kosten für Management, Datenverkehr und Sicherheitsfeatures.
   - wie Zoho CRM und Salesforce haben diese Features in ihren Plänen, sind jedoch weniger flexibel in Bezug auf Anpassungen.

---

- **Günstigste Optionen**: Heroku und Azure.
- **Minimalster Aufwand**: Zoho CRM und Salesforce.
- **Langfristige Flexibilität**: AWS oder Azure.

---

## Meine Empfehlung
- Wenn ihr die **Flexibilität** und die Kontrolle wichtig ist, würde ich AWS oder Azure wählen. Wenn es dann noch um den Preis geht, würde ich Azure empfehlen.  
- Wenn ihr Fokus auf **geringem Aufwand** und schnellem Zugang zu einem CRM liegt, würde ich **Zoho CRM** wählen, da es kostengünstiger als Salesforce ist und alle erforderlichen Funktionen bietet.  
- Für eine Mischung aus moderatem Aufwand und fertigen Entwicklungsumgebungen empfehle ich **Heroku**.