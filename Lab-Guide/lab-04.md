## Inhalt
Einführung

Dataflow Gen2
  - Aufgabe 1: Snowflake-Abfragen in Dataflow kopieren
  - Aufgabe 2: Verbindung zu Snowflake erstellen
  - Aufgabe 3: Datenziel für die Abfragen „Supplier“ und „PO“ konfigurieren
  - Aufgabe 4: Snowflake-Dataflow umbenennen und veröffentlichen
  - Aufgabe 5: Dataverse-Abfragen in Dataflow kopieren	
  - Aufgabe 6: Verbindung zu Dataverse erstellen	
  - Aufgabe 7: Datenziel für die Abfrage „Customer“ erstellen	
  - Aufgabe 8: Dataverse-Dataflow veröffentlichen und umbenennen	
  - Aufgabe 9: SharePoint-Abfragen in Dataflow kopieren	
  - Aufgabe 10: Verbindung zu SharePoint erstellen	
  - Aufgabe 11: Datenziel für die Abfrage „People“ konfigurieren	
  - Aufgabe 12: SharePoint-Dataflow veröffentlichen und umbenennen
	
Referenzen	

## Einführung
Bei unserem Anwendungsfall befinden sich die Lieferantendaten in Snowflake, die Kundendaten in Dataverse und die Mitarbeiterdaten in SharePoint. Alle diese Datenquellen werden zu verschiedenen Zeiten aktualisiert. Um die Anzahl der Datenaktualisierungen von Dataflows zu verringern, erstellen wir für jede dieser Datenquellen individuelle Dataflows.
**Hinweis:** Ein einziger Dataflow berücksichtigt dabei mehrere Datenquellen. Inhalt dieser Übung:
  - Mit Dataflow Gen2 eine Verbindung zu Snowflake herstellen und Daten im Lakehouse erfassen
  - Mit Dataflow Gen2 eine Verbindung zu SharePoint herstellen und Daten im Lakehouse erfassen
  - Mit Dataflow Gen2 eine Verbindung zu Dataverse herstellen und Daten im Lakehouse erfassen

## Dataflow Gen2
### Aufgabe 1: Snowflake-Abfragen in Dataflow kopieren
1.	Navigieren wir nun zurück zum Fabric-Arbeitsbereich, **FAIAD_<username>**, den Sie in Übung 2, Aufgabe 9, erstellt haben.
2.	Wählen Sie im Menü oben die Option **Neu -> Dataflow Gen2** aus.

Sie werden zur Dataflow-Seite weitergeleitet. Nachdem Sie Dataflow nun kennen, kopieren Sie die Abfragen aus Power BI Desktop in Dataflow.

3.	Öffnen Sie **FAIAD.pbix** im Ordner **C:\FAIAD\Reports** in Ihrer Übungsumgebung, falls dies noch nicht erfolgt ist.
4.	Wählen Sie im Menüband **Start > Daten transformieren** aus. Das Power Query-Fenster wird
geöffnet. Wie Sie in der vorherigen Übung festgestellt haben, sind die Abfragen im linken Bereich nach Datenquelle organisiert.
5.	Das Power Query-Fenster wird geöffnet. Wählen Sie links unter dem Ordner „SnowflakeData“ mit
**Strg+Auswahl** oder „Umschalt+Auswahl“ die folgenden Abfragen aus:<BR>
&nbsp; &nbsp; a.	SupplierCategories<BR>
&nbsp; &nbsp; b.	Suppliers<BR>
&nbsp; &nbsp; c.	Supplier<BR>
&nbsp; &nbsp; d.	PO<BR>
&nbsp; &nbsp; e.	PO Line Items

6.	**Klicken Sie mit der rechten Maustaste**, und wählen Sie **Kopieren** aus.
7.	Navigieren Sie zurück zum **Browser**.
8.	Wählen Sie im Bereich **Dataflow** den **mittleren Bereich** aus, und drücken Sie **Strg+V** (das Einfügen mittels Rechtklick ist derzeit nicht möglich). Wenn Sie ein MAC-Gerät verwenden, drücken Sie zum Einfügen bitte Cmd+V.

**Hinweis:** Wenn Sie in der Übungsumgebung arbeiten, wählen Sie die Auslassungspunkte oben rechts auf dem Bildschirm aus. Verwenden Sie den Schieberegler, um das **VM Native Clipboard zu aktivieren**. Wählen Sie im Dialogfeld OK aus. Nachdem Sie die Abfragen eingefügt haben, können Sie diese Option deaktivieren.

### Aufgabe 2: Verbindung zu Snowflake erstellen
Beachten Sie, dass die fünf Abfragen eingefügt wurden und dass der Bereich „Abfragen“ jetzt links ist. Weil für Snowflake keine Verbindung erstellt wurde, wird eine Warnmeldung angezeigt, in der Sie aufgefordert werden, eine Verbindung zu konfigurieren.
1.	Wählen Sie **Verbindung konfigurieren** aus.
2.	Das Dialogfeld „Mit Datenquelle verbinden“ wird geöffnet. Überprüfen Sie, dass im Dropdown- Menü **Verbindung** die Option **Neue Verbindung erstellen** ausgewählt ist.
3.	Die **Authentifizierungsart** sollte **Snowflake** lauten.
4.	Geben Sie den **Benutzernamen und das Kennwort für Snowflake** ein. Beides finden Sie auf der Registerkarte mit den Environment Variables (neben der Registerkarte mit der Übungsanleitung).
5.	Wählen Sie **Verbinden** aus.

Die Verbindung wird hergestellt, und Sie können die Daten im Vorschaufenster ansehen. Wenn Sie möchten, sehen Sie sich die angewandten Schritte der Abfragen an. Grundsätzlich enthält die Suppliers-Abfrage Lieferanteninformationen und „SupplierCategories“, wie der Name schon sagt, Lieferantenkategorien. Diese beiden Tabellen werden zusammengeführt, um die Dimension „Supplier“ mit den erforderlichen Spalten zu erstellen. Auf ähnliche Weise wird „PO Line Items“ mit „PO“ zusammengeführt, um den Fakt „PO“ zu erstellen. Nun müssen die Daten von „Supplier“ und „PO“ im Lakehouse erfasst werden.

6.	Wie bereits erwähnt, stellen wir keine dieser Daten bereit. Klicken Sie im Bereich mit den
Abfragen **mit der rechten Maustaste** auf die Abfrage **Supplier**, und wählen Sie **Staging aktivieren**
aus, um das Häkchen zu entfernen.

