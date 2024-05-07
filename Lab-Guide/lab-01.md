## Inhalt

- Dokumentstruktur

- Anwendungsfall/Problemstellung

- Überblick über den Power BI Desktop-Bericht

    - Aufgabe 1: Power BI Desktop in einer Übungsumgebung einrichten

    - Aufgabe 2: Power BI Desktop-Bericht analysieren

    - Aufgabe 3: Power Query-Abfragen überprüfen

- Referenzen

## Dokumentstruktur

Die Übung enthält die Schritte, die der Benutzer durchführen muss, sowie zugehörige Screenshots zur visuellen Unterstützung. Wichtige Abschnitte sind in den Screenshots mit einem orangefarbenen Kasten gekennzeichnet.

## Anwendungsfall/Problemstellung
Fabrikam, Inc. vertreibt Livestyle-Artikel. Die Kunden von Fabrikam sind zumeist Unternehmen, die die Artikel an den Endverbraucher weiterverkaufen. Fabrikam verkauft an Einzelhandelskunden in den USA, darunter Fachgeschäfte, Supermärkte, Computergeschäfte und Souvenirläden. Fabrikam vertreibt seine Waren über ein Netzwerk von Vertretern, die die Produkte im Namen von Fabrikam bewerben, auch an andere Großhändler. Derzeit sind alle Kunden von Fabrikam in den USA ansässig. Das Unternehmen plant aber eine Expansion in andere Länder oder Regionen.

Sie arbeiten als Data Analyst im Vertriebsteam. Ihre Aufgabe ist das Sammeln, Bereinigen und
Auswerten von Datasets zur Lösung geschäftlicher Probleme. Außerdem fertigen Sie Diagramme und Visualisierungen an, schreiben Berichte und präsentieren diese den Entscheidungsträgern in der Organisation.

Um wertvolle Erkenntnisse aus den Daten zu ziehen, rufen Sie Daten aus mehreren Systemen ab, bereinigen diese und führen sie zusammen. Dabei beziehen Sie folgende Daten aus folgenden Quellen:

- **Vertriebsdaten**: Diese stammen aus dem ERP-System und werden in einer ADLS Gen2-Datenbank oder in Databricks abgelegt. Jeden Tag um 12 Uhr mittags werden die Daten aktualisiert.
- **Lieferantendaten**: Diese kommen von verschiedenen Lieferanten und werden in einer Snowflake-Datenbank gespeichert. Jeden Tag um Mitternacht werden die Daten aktualisiert.
- **Kundendaten**: Diese stammen aus Customer Insights und werden in Dataverse gespeichert. Die Daten sind immer auf dem neuesten Stand.
- **Mitarbeiterdaten**: Diese stammen aus dem Personalsystem und werden als Exportdatei in einem SharePoint-Ordner gespeichert. Die Daten werden jeden Morgen um 9 Uhr aktualisiert.

Derzeit arbeiten Sie an einem Dataset in Power BI Premium, mit dem die Daten aus den oben
genannten Quellsystemen abgerufen werden sollen, damit Sie Ihre Berichte schreiben können und Endanwender die Möglichkeit erhalten, Self-Service-Angebote zu nutzen. Das Modell aktualisieren Sie mit Power Query.

### Nun sind Sie mir folgenden Problemen konfrontiert:

- Das Dataset muss mindestens dreimal täglich aktualisiert werden, um den verschiedenen Aktualisierungszeiten der Datenquellen Rechnung zu tragen.

- Die Aktualisierungen dauern lange, weil die Daten jedes Mal komplett aktualisiert werden müssen, um alle Änderungen an den Daten in den Quellsystemen zu erfassen.

- Tritt in den Datenquellen, aus denen die Daten abgerufen werden, ein Fehler auf, wird
die DataSet-Aktualisierung abgebrochen. Oftmals wird die Mitarbeiterdatei nicht pünktlich hochgeladen, was ebenso zum Abbruch der DataSet-Aktualisierung führt.

- Änderungen am Datenmodell nehmen sehr viel Zeit in Anspruch, weil Power Query aufgrund der großen Datenmenge und des aufwändigen Transformationsvorgangs sehr lange braucht, um die Vorschauversionen zu aktualisieren.

- Für Power BI Desktop brauchen Sie einen PC mit Windows, auch wenn im Unternehmen Mac-Geräte genutzt werden.

Sie haben von Microsoft Fabric gehört und möchten es gerne ausprobieren, um all diese Probleme zu lösen.
