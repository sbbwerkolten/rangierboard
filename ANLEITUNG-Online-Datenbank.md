# Online-Datenbank für die Vorführung (Firebase, kostenlos)

Damit alle Geräte denselben Stand sehen, speichert die App Fahrzeuge, Aufträge, Mitarbeiter,
Rollen, Abwesenheiten und Schichtplan in einer kostenlosen Firebase-Datenbank.
Layouts und Anmeldung bleiben pro Gerät.

## 1. Datenbank anlegen (ca. 5 Minuten)
1. Auf https://console.firebase.google.com mit einem Google-Konto anmelden.
2. «Projekt hinzufügen», Namen vergeben (z. B. rangierboard), Google Analytics ausschalten.
3. Links «Build» → «Realtime Database» → «Datenbank erstellen».
   Standort: **europe-west1 (Belgien)**. Start im **gesperrten Modus**.
4. Oben auf den Reiter **«Regeln»** wechseln, alles ersetzen durch:

   { "rules": { "rb": { ".read": true, ".write": true } } }

   und «Veröffentlichen» klicken.
5. Oben im Reiter **«Daten»** steht die Adresse der Datenbank, z. B.
   `https://rangierboard-default-rtdb.europe-west1.firebasedatabase.app`
   Diese Adresse kopieren (ohne Schrägstrich am Ende).

## 2. Adresse in die App eintragen
- Im GitHub-Repository die Datei `config.json` öffnen (Stift-Symbol) und ändern in:

  { "dbUrl": "https://DEINE-ADRESSE" }

  Mit «Commit changes» speichern. Nach 1 bis 2 Minuten gilt es für alle Geräte.
- Zum schnellen Testen auf einem einzelnen Gerät geht auch: Seite einmal mit
  `?db=https://DEINE-ADRESSE` am Ende der Webadresse öffnen. Das merkt sich das Gerät.

## 3. Prüfen
Im Menü (oben rechts) steht «Mit der Online-Datenbank verbunden». Auf einem zweiten Gerät
dieselbe Seite öffnen: Fahrzeuge und Aufträge erscheinen dort nach wenigen Sekunden.

## Hinweise
- Das erste Gerät, das sich mit der leeren Datenbank verbindet, legt seinen Stand dort ab.
  Weitere Geräte übernehmen den Stand der Datenbank (lokale Aufträge werden ersetzt).
- «Daten löschen» gilt dann für alle Geräte.
- Die Regeln oben erlauben jedem, der die Adresse kennt, Lesen und Schreiben. Das ist nur für
  die Vorführung gedacht: keine echten Daten eintragen, die Datenbank danach löschen.
- Ohne Verbindung arbeitet ein Gerät weiter und gleicht später nach.
