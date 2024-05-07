## Inhalt
- Einführung
- Dataflow Gen2
  - Aufgabe 1: Dataflow Gen2 erstellen
  - Aufgabe 3: Die Abfrage für den Ordner „Base ADLS Gen2“ erstellen
  - Aufgabe 2: Verbindung zu ADLS Gen2 herstellen
  - Aufgabe 4: Abfrage „Cities“ erstellen
  - Aufgabe 5: Abfrage „Countries“ erstellen
  - Aufgabe 6: States mit Kopieren – Option 1 erstellen
  - Aufgabe 7: Abfrage „Geo“ mit Kopieren erstellen – Option 2
  - Aufgabe 8: Datenziel für die Abfrage „Geo“ konfigurieren
  - Aufgabe 9: Dataflow veröffentlichen
  - Aufgabe 10: Dataflow umbenennen
  - Aufgabe 11: Verbleibende Abfragen im Dataflow erstellen
  - Aufgabe 12: Datenziel für verbleibende Abfragen konfigurieren
- Referenzen

## Einführung
In unserem Szenario stammen die Verkaufsdaten aus dem ERP-System und werden in einer ADLS Gen2 gespeichert. Jeden Tag um 12 Uhr mittags werden die Daten aktualisiert. Wir müssen diese Daten transformieren, in Lakehouse erfassen und in unserem Modell verwenden.

Es gibt mehrere Möglichkeiten, diese Daten zu erfassen.



- **Verknüpfungen**: Hiermit können keine Daten transformiert werden.
- **Notebooks**: Dafür müssen wir Code schreiben. Es handelt sich um einen entwicklerfreundlichen Ansatz.
- **Dataflow** Gen2: Sie sind wahrscheinlich mit Power Query oder Dataflow Gen1 vertraut. Dataflow Gen2 ist, wie der Name schon sagt, die neuere Version von Dataflow. Es bietet alle Funktionen von Power Query/Dataflow Gen1 und ermöglicht zusätzlich die Transformation und Erfassung von Daten in mehreren Datenquellen. Wir werden dies in den nächsten
Übungen vorstellen.
- **Datenpipeline**: Dies ist ein Orchestrierungstool. Aktivitäten können orchestriert werden, um Daten zu extrahieren, zu transformieren und zu erfassen. Wir werden Data Pipeline verwenden, um Dataflow Gen2-Aktivitäten auszuführen, die wiederum Extraktion, Transformation und Aufnahme durchführen.

Wir beginnen mit Dataflow Gen2, um eine Verbindung zur Datenquelle und den notwendigen Transformationen herzustellen. Dann werden wir Dataflow Gen2 mit Data Pipeline
orchestrieren/ausführen. 

Inhalt dieser Übung:
  - So erstellen Sie Dataflow Gen2
  - So stellen Sie mithilfe von Dataflow Gen2 eine Verbindung zu ADLS Gen2 her und transformieren Daten
  - So erfassen Sie Daten in Lakehouse

## Dataflow Gen2
### Aufgabe 1: Dataflow Gen2 erstellen

1.	Navigieren wir zurück zum Fabric-Arbeitsbereich, den Sie in Übung 2, Aufgabe 9, erstellt haben.
2.	Wenn Sie nach der vorherigen Übung nicht zu einem anderen Bereich navigiert sind, befinden Sie sich im Lakehouse-Bildschirm. Wählen Sie unten links auf dem Bildschirm das Symbol Fabric- Funktionsbereichs-Auswahl aus.
3.	Wählen Sie im geöffneten Dialogfeld für den Fabric-Funktionsbereich Data Factory aus. Data Factory verfügt über Workloads, die zum Extrahieren, Transformieren und Erfassen von Daten erforderlich sind.
4.	Sie werden zur Data Factory-Startseite weitergeleitet. Wählen Sie unter „Neu“ die Option
Datenfluss Gen2 aus.

Sie werden zur **Dataflow-Seite** weitergeleitet. Dieser Bildschirm wird Ihnen bekannt vorkommen, da er Dataflow Gen1 oder Power Query ähnelt. Sie werden feststellen, dass die Optionen zum Herstellen einer Verbindung zu verschiedenen Datenquellen sowie die Möglichkeit zur Datentransformation verfügbar sind. Stellen wir eine Verbindung zur ADLS Gen2-Datenquelle her und führen einige Transformationen durch.

### Aufgabe 2: Verbindung zu ADLS Gen2 herstellen

1.	Wählen Sie im Menüband **Start -> Daten abrufen -> Mehr…**
2.	Sie werden zum Dialogfeld **Daten abrufen Datenquelle auswählen** weitergeleitet. Sie können nach der Datenquelle suchen, indem Sie sie in das Suchfeld eingeben. Beachten Sie, dass im
linken Bereich Optionen zur Verwendung einer Blank-Tabelle oder Blank-Abfrage vorhanden ist. Es ist außerdem eine neue Option zum Hochladen von Dateien verfügbar. Wir werden diese Option in einer späteren Übung untersuchen. Klicken wir zunächst oben rechts im Bildschirm auf **Mehr anzeigen ->**.

Jetzt können Sie alle verfügbaren Datenquellen anzeigen. Sie haben die Möglichkeit, die Datenquellen nach Datei, Datenbank, Microsoft Fabric, Power Platform, Azure usw. zu filtern.

3.	Wählen Sie **Azure** aus den oberen Filteroptionen aus, um nach Azure-Datenquellen zu filtern.
4.	Wählen Sie **Azure Data Lake Storage Gen2** aus.
5.	Sie werden zum Dialogfeld „Mit Datenquelle verbinden“ weitergeleitet. Sie müssen eine Verbindung zur ADLS Gen2-Datenquelle herstellen. Geben Sie unter **Verbindungseinstellungen -> URL** diesen Link https://stvnextblobstorage.dfs.core.windows.net/fabrikam-sales/Delta-Parquet-Format ein.
6.	Wählen Sie **Kontoschlüssel** aus der Dropdown-Liste „Authentifizierungsart“ aus.
7.	Kopieren Sie den **Zugriffsschlüssel für das Adls-Speicherkonto** von der Registerkarte **Umgebungsvariablen** (neben der Registerkarte „Übungsanleitung“) und fügen Sie ihn in das Textfeld **Kontoschlüssel** ein.
8.	Wählen Sie unten rechts auf dem Bildschirm **Weiter** aus.

### Aufgabe 3: Die Abfrage für den Ordner „Base ADLS Gen2“ erstellen

1.	Sobald die Verbindung hergestellt ist, werden Sie zum Bildschirm **Vorschau der Ordnerdaten anzeigen** weitergeleitet. Im ADLS Gen2-Ordner sind viele Dateien enthalten. Wir benötigen Daten aus einigen von ihnen. Wählen Sie **Erstellen** aus, um eine Verbindung zum Ordner herzustellen.
2.	Sie befinden sich wieder im Dialogfeld **Power Query**. Dies ist die Verbindung zum Stammordner von ADLS Gen2. Wir werden in nachfolgenden Abfragen auf diese Abfrage verweisen. Wir benennen die Abfrage um. Ändern Sie im **rechten Bereich** unter **Abfrageeinstellungen -> Eigenschaften -> Name** den Namen in **ADLS Base Folder for Geo**.
3.	Alle Abfragen von Dataflow Gen2 werden standardmäßig in ein Staging Lakehouse geladen. Im Rahmen dieser Übung werden wir keine Daten bereitstellen. Klicken Sie im **linken Bereich mit der rechten Maustaste auf die Abfrage „ADLS Base Folder“**, um diesen Ladevorgang zu deaktivieren.

**Hinweis:** Staging wird verwendet, wenn wir Daten für die weitere Transformation bereitstellen müssen, bevor sie für die Nutzung bereit sind.

4.	**Deaktivieren Sie die Option „Staging aktivieren“**.

Beachten Sie, dass der Ordner zwei Dateiformate enthält: **JSON** und **Parquet**.
  - **Parquet**: ist ein Open-Source-Dateiformat, das für die Verarbeitung einfacher spaltenorientierter Speicherdatenformate entwickelt wurde. Parquet funktioniert gut mit komplexen Daten in großen Mengen und ist sowohl für seine leistungsstarke Datenkomprimierung als auch für
seine Fähigkeit bekannt, eine Vielzahl von Codierungstypen zu verarbeiten.
  - **JSON**: Diese Datei enthält Metadaten wie Schema, Datentyp der Parquet-Datei.

5.	Wir benötigen lediglich die Parquet-Datei, da diese die von uns benötigten Daten enthält. Wählen Sie den **Dropdown-Pfeil Extension** aus.
6.	**Deaktivieren Sie .json**, sodass sie nach .parquet-Dateien gefiltert wird.
7.	Wählen Sie **OK** aus.

Jetzt haben wir die Abfrage „Base“ eingerichtet. Wir können diese Abfrage für alle Geo-Abfragen referenzieren.

### Aufgabe 4: Abfrage „Cities“ erstellen
Verkaufsdaten sind nach Geografie, Produkt, Verkäufer und Datengranularität verfügbar. Erstellen wir zunächst eine Abfrage, um die Geo-Dimension zu erhalten. Geodaten sind in drei verschiedenen Dateien verfügbar, die sich in den folgenden Unterordnern befinden:
  - **Cities**: Application.Cities
  - **Countries**: Application.Countries
  - **State**: Application.StateProvinces

Wir müssen City-, State- und Country-Daten aus diesen drei Dateien kombinieren, um die Geo- Dimension zu erstellen.
1.	Beginnen wir mit „City“. Klicken Sie im linken Bereich **mit der rechten Maustaste auf „ADLS Base Folder for Geo“**. Wählen Sie **Verweis** aus, um eine neue Abfrage zu erstellen, die auf die Abfrage
„ADLS Base Folder for Geo“ verweist.
2.	Wählen Sie den **Dropdown-Pfeil der Spalte Folder Path** aus.
3.	Wählen Sie **Textfilter -> Enthält…** aus.
4.	Geben Sie im Dialog **Zeilen filtern Application.Cities** ein.

**Hinweis**: Hier müssen Sie die Groß- und Kleinschreibung beachten.

5.	Wählen Sie **OK** aus.
6.	Daten werden in einer einzelne Zeile gefiltert. Wählen Sie **Binary** unter der Spalte **Content** aus.
7.	Beachten Sie, dass alle City-Details angezeigt werden. Ändern Sie im **rechten Bereich** unter **Abfrageeinstellungen -> Eigenschaften -> Name den Namen** in **Cities**.

**Hinweis**: Stellen Sie unten rechts im Screenshot sicher, dass die Abfrage über vier angewendete Schritte verfügt, und warten Sie, bis sie vollständig geladen ist. Dies kann einige Minuten dauern.

Beachten Sie im rechten Bereich unter **Angewendete Schritte**, dass alle Schritte registriert sind. Dieses Verhalten ist mit dem von Power Query identisch. Folgen wir nun einem ähnlichen Prozess, um die Abfrage **Country** zu erstellen.

### Aufgabe 5: Abfrage „Countries“ erstellen

1.	Klicken Sie im linken Bereich **mit der rechten Maustaste auf „ADLS Base Folder for Geo“**. Wählen Sie **Verweis** aus, um eine neue Abfrage zu erstellen, die auf die Abfrage „ADLS Base Folder for Geo“ verweist.
2.	Wählen Sie den **Dropdown-Pfeil** der** Spalte Folder Path** aus.
3.	Wählen Sie **Textfilter -> Enthält…** aus.
4.	Geben Sie im **Dialogfeld „Zeilen filtern“ Application.Countries** ein.

**Hinweis**: Hierbei muss die Groß-/Kleinschreibung beachtet werden.

5.	Wählen Sie **OK** aus.
6.	Daten werden in einer einzelne Zeile gefiltert. Wählen Sie **Binary** unter der Spalte **Content** aus
7.	Beachten Sie, dass alle Country-Details angezeigt werden. Ändern Sie im **rechten Bereich** unter **Abfrageeinstellungen -> Eigenschaften -> Name** den Namen in **Countries**.

**Hinweis**: Stellen Sie unten rechts im Screenshot sicher, dass die Abfrage über vier angewendete Schritte verfügt, und warten Sie, bis sie vollständig geladen ist. Dies kann einige Minuten dauern.

Als Nächstes müssen wir „State“ einfügen, aber die Schritte wiederholen sich immer mehr. Wir verfügen bereits über die Abfragen in der Power BI Desktop-Datei. Jetzt prüfen wir, ob wir die Abfragen von dort kopieren können.

### Aufgabe 6: States mit Kopieren – Option 1 erstellen
1.	Öffnen Sie **FAIAD.pbix** im Ordner **C:\FAIAD\Reports** in Ihrer Übungsumgebung, falls dies noch nicht erfolgt ist.
2.	Wählen Sie im Menüband **Start > Daten transformieren** aus. Das Power Query-Fenster wird
geöffnet. Wie Sie in der vorherigen Übung festgestellt haben, sind die Abfragen im linken Bereich nach Datenquelle organisiert.
3.	Klicken Sie im linken Bereich unter dem ADLSData-Ordner **mit der rechten Maustaste auf die Abfrage „States“**, und wählen Sie **Kopieren** aus.
4.	Navigieren Sie zurück zum **Browser**. Sie sollten sich im Dataflow befinden, an dem wir gearbeitet haben.
5.	Wählen Sie im linken Bereich den Bereich **Abfragen** aus, und geben Sie **STRG+V** ein (derzeit wird das Einfügen mit der rechten Maustaste nicht unterstützt). Wenn Sie ein MAC-Gerät verwenden, drücken Sie zum Einfügen bitte Cmd+V.

**Hinweis:** Wenn Sie in der Übungsumgebung arbeiten, wählen Sie die Auslassungspunkte oben rechts auf dem Bildschirm aus. Verwenden Sie den Schieberegler, um das **VM Native Clipboard zu
aktivieren**. Wählen Sie im Dialogfeld OK aus. Nachdem Sie die Abfrage eingefügt haben, können Sie diese Option deaktivieren.

Beachten Sie, dass „ADLS Base Folder“ ebenfalls kopiert wird. Dies liegt daran, dass sich die Abfrage
„States“ auf „ADLS Base Folder“ in Power BI Desktop bezieht, wir aber bereits über eine ähnliche Abfrage verfügen. Lassen Sie uns dies lösen.

6.	Wählen Sie die Abfrage **States** aus.
7.	Wählen Sie im **rechten Bereich** unter **Angewendete Schritte** die Option **Source** aus.
8.	Ändern Sie in der Formelleiste #”ADLS Base Folder” zu **#”ADLS Base Folder for Geo”**.
9.	Klicken Sie auf das **Häkchen** neben der Bearbeitungsleiste, oder drücken Sie die **Eingabetaste**.
10.	Jetzt können wir „ADLS Base Folder“ entfernen. Klicken Sie im linken Bereich unter dem Abschnitt **Abfragen mit der rechten Maustaste auf die Abfrage ADLS Base Folder**, und wählen Sie **Löschen** aus.
11.	Das Dialogfeld „Abfrage löschen“ wird angezeigt. Wählen Sie zur Bestätigung **Löschen** aus.

**Hinweis:** Stellen Sie sicher, dass die Abfrage über vier angewendete Schritte verfügt, und warten Sie, bis die Abfrage vollständig geladen ist. Dies kann einige Minuten dauern.

### Aufgabe 7: Abfrage „Geo“ mit Kopieren erstellen – Option 2

Jetzt müssen wir diese Abfragen zusammenführen, um die Geo-Dimension zu erstellen. Wir kopieren die Abfrage erneut aus der Datei Power BI Desktop. Dieses Mal kopieren wir den Code aus dem
erweiterten Editor.

1.	Navigieren Sie zurück zum **Power Query-Fenster** der Power BI Desktop-Datei.
2.	Wählen Sie im linken Bereich unter **Abfragen** die Abfrage **Geo** im Ordner „ADLSData“ aus.
3.	Wählen Sie im Menüband die Registerkarte **Start -> Erweiterter Editor** aus.
4.	Das Fenster „Erweiterter Editor“ wird geöffnet. **Heben Sie den gesamten Text** im erweiterten Editor hervor.
5.	**Klicken Sie mit der rechten Maustaste**, und wählen Sie **Kopieren** aus.
6.	Klicken Sie oben rechts im Fenster auf **X**, oder wählen Sie die Option **Fertig** aus, um das Fenster
„Erweiterter Editor“ zu schließen.
7.	Navigieren Sie im Browser zurück zum Fenster **Dataflow**.
8.	Klicken Sie im Menüband auf **Daten abrufen > Leere Abfrage**.
9.	Rufen Sie die Daten ab. Der Dialog „Erweiterter Editor“ mit der Option „Mit Datenquelle verbinden“ wird geöffnet. **Heben Sie den gesamten Text** im Editor hervor.
10.	Wählen Sie auf Ihrer Tastatur **Löschen** aus, um den gesamten Text zu löschen.
11.	Der erweiterte Editor sollte leer sein. Geben Sie nun **STRG+V** ein, um den Inhalt einzufügen, den Sie aus dem erweiterten Editor von Power BI Desktop kopiert haben.
12.	Wählen Sie **Weiter** aus.
13.	Jetzt verfügen wir über die Geo-Dimension. Wir benennen die Abfrage um. Ändern Sie im
**rechten Bereich** unter **Abfrageeinstellungen -> Eigenschaften -> Name** den Namen in **Geo**.

**Hinweis:** Warten Sie, bis die Abfrage vollständig geladen ist. Dies kann einige Minuten dauern.Gehen wir die Schritte durch, um zu verstehen, wie Geo erstellt wurde. Wählen Sie im rechten
Bereich unter „Angewendete Schritte“ die Option **Quelle** aus. Wenn Sie sich die Bearbeitungsleiste ansehen oder auf „Einstellungen“ klicken, stellen Sie fest, dass die Quelle dieser Abfrage eine
Verknüpfung zwischen Cities und States ist. Wenn Sie die Schritte durchgehen, stellen Sie fest, dass das Ergebnis der ersten Verknüpfung wiederum mit „Countries“ verknüpft wird. Daher werden alle drei Abfragen verwendet, um eine Geo-Dimension zu erstellen.

### Aufgabe 8: Datenziel für die Abfrage „Geo“ konfigurieren
Jetzt verfügen wir über eine Dimension. Lassen Sie uns diese Daten in Lakehouse erfassen. Dies ist die neue Funktion, die in Dataflow Gen2 verfügbar ist.
1.	Wie bereits erwähnt, stellen wir keine dieser Daten bereit. Klicken Sie also **mit der rechten Maustaste** auf die Abfrage **Cities**, und wählen Sie **Staging aktivieren** aus, um das Häkchen zu entfernen.
2.	Befolgen Sie dieselben Schritte für die Abfrage **Countries und Geo**, um **das Häkchen neben Staging aktivieren** zu entfernen.
3.	Wählen Sie die Abfrage **Geo** aus.
4.	Wählen Sie unten rechts „+“ neben **Datenziel** aus.
5.	Wählen Sie im Dialogfeld die Option **Lakehouse** aus.
6.	Das Dialogfeld „Herstellen einer Verbindung mit dem Datenziel“ wird geöffnet. Wir müssen eine neue Verbindung zu Lakehouse herstellen. Wenn **Neue Verbindung erstellen** im **Dropdown-Menü „Verbindung“** ausgewählt und **Authentifizierungsart** auf **Organisationskonto** festgelegt ist, wählen Sie **Weiter** aus.
7.	Nachdem die Verbindung hergestellt wurde, wird das Dialogfeld „Ziel auswählen“ geöffnet.
Stellen Sie sicher, dass das **Optionsfeld „Neue Tabelle“** ausgewählt ist, da wir eine neue Tabelle erstellen.
8.	Wir möchten die zuvor erstellte Tabelle in Lakehouse erstellen. Navigieren Sie im linken Bereich zu **Lakehouse -> FAIAD_<Benutzername>.**
9.	Wählen Sie **lh_FAIAD** aus.
10.	Behalten Sie den Tabellennamen **Geo** bei.
11.	Wählen Sie **Weiter** aus.
12.	Das Dialogfeld „Zieleinstellungen auswählen“ wird geöffnet. Verwenden Sie den **Schieberegler**, um **automatische Einstellungen zu deaktivieren**. Schauen wir uns die Optionen an.
Beachten Sie, dass es Optionen zum **Anfügen von Daten** an eine vorhandene Tabelle oder zum
**Ersetzen** gibt.
Beachten Sie außerdem, dass es für **das Veröffentlichen Schemaoptionen** gibt.
Sie haben die Möglichkeit, das Schema unverändert zu lassen. Wenn es sich im Laufe der Zeit ändern soll, steht Ihnen die Option eines dynamischen Schemas zur Verfügung.
Sie haben die Möglichkeit, das Schema unverändert zu lassen. Lakehouse unterstützt keine Spaltennamen mit Leerzeichen. Wenn Sie „Korrigieren“ auswählen, werden Leerzeichen in Spaltennamen durch Unterstriche ersetzt.

**Hinweis:** Mit dem Kontrollkästchen rechts neben der Spalte „Quelle” können Sie nur die Spalten auswählen, die Sie in Lakehouse laden möchten.

13.	In unserem Szenario verwenden wir automatische Einstellungen. Aktivieren Sie den Schieberegler **Automatische Einstellungen aktivieren**. Beachten Sie, dass damit die Zielspaltennamen automatisch mit einem Unterstrich korrigiert werden.
14.	Mithilfe der Spaltenzuordnung können Dataflow-Spalten vorhandenen Spalten zugeordnet werden. In unserem Fall handelt es sich um eine neue Tabelle. Daher können wir die Standardwerte verwenden. Wählen Sie **Einstellungen speichern** aus.

### Aufgabe 9: Dataflow veröffentlichen
1.	Sie werden zum **Power Query-Fenster** weitergeleitet. Beachten Sie, dass unten rechts das
**Datenziel auf Lakehouse festgelegt ist**.
2.	Lassen Sie uns diese Abfragen veröffentlichen, damit wir Lakehouse überprüfen können. Wir werden darauf zurückkommen, um weitere Abfragen hinzuzufügen. Wählen Sie unten rechts **Veröffentlichen** aus.
3.	Sie werden zum Arbeitsbereich **FAIAD_<Benutzername>** weitergeleitet. Es kann einige
Momente dauern, bis der Dataflow veröffentlicht wird. Wählen Sie anschließend entweder aus dem mittleren oder dem linken Bereich **lh_FAIAD Lakehouse aus**.
4.	Sie werden zum **Bildschirm „Lakehouse-Explorer“** weitergeleitet. Erweitern Sie im linken Bereich die Option **lh_FAIAD -> Tables**.
5.	Beachten Sie, dass jetzt eine Geo-Tabelle in Lakehouse vorhanden ist. Erweitern Sie **Geo**, und beachten Sie alle Spalten.
6.	**Wählen Sie die Geo-Tabelle** aus, sodass die Datenvorschau im rechten Bereich geöffnet wird.

Es ist auch ein SQL-Endpunkt vorhanden, der zum Abfragen dieser Tabelle verwendet werden kann. Wir sehen uns diese Option in einer späteren Übung an. Da wir nun wissen, dass die Geodaten in Lakehouse vorhanden sind, fügen wir die restlichen Daten von ADLS Gen2 ein.


### Aufgabe 10: Dataflow umbenennen
1.	Wählen Sie in der linken Menüleiste **FAIAD_<Benutzername>** aus, um zum **Arbeitsbereich**
zurückzukehren.
2.	Wir arbeiten mit Dataflow 1. Benennen wir es um, bevor wir fortfahren. Klicken Sie auf die
**Auslassungspunkte (…)** neben Dataflow 1. Wählen Sie **Eigenschaften** aus.
3.	Das Dialogfeld „Dataflow-Eigenschaften“ wird geöffnet. Ändern Sie den Namen in **df_Sales_ADLS**.

**Hinweis:** Wir stellen dem Dataflow-Namen „**df**“ voran. Dadurch kann er einfacher gesucht und sortiert werden.

4.	Fügen Sie im Textfeld **Beschreibung den Text Dataflow to ingest Sales Data from ADLS to Lakehouse hinzu**.
5.	Wählen Sie **Speichern** aus.

### Aufgabe 11: Verbleibende Abfragen im Dataflow erstellen
1.	Sie werden zum Arbeitsbereich **FAIAD_<Benutzername>** weitergeleitet. Wählen Sie den Dataflow **df_Sales_ADLS** aus, um zum Dataflow zurückzukehren.

Zur Vereinfachung prüfen wir jetzt, ob wir die Abfragen aus Power BI Desktop kopieren können.

2.	Öffnen Sie **FAIAD.pbix** im Ordner **C:\FAIAD\Reports** in Ihrer Übungsumgebung, falls dies noch nicht erfolgt ist.
3.	Wählen Sie im Menüband **Start > Transformieren** aus. Das Power Query-Fenster wird geöffnet.
4.	Wählen Sie im Bereich **Abfragen** auf der linken Seite mit **STRG+Auswahl** die folgenden Abfragen aus **ADLSData** aus.<br>
&nbsp; &nbsp; a.	Product<br>
&nbsp; &nbsp; b.	Product Groups<br>
&nbsp; &nbsp; c.	Product Item Group<br>
&nbsp; &nbsp; d.	Product Details<br>
&nbsp; &nbsp; e.	Invoice<br>
&nbsp; &nbsp; f.	InvoiceLineItems<br>
&nbsp; &nbsp; g.	Sales<br>
&nbsp; &nbsp; h.	BuyingGroup<br>
&nbsp; &nbsp; i.	Reseller<br>
&nbsp; &nbsp; j.	Date<br>
5.	**Klicken Sie mit der rechten Maustaste**, und wählen Sie **Kopieren** aus.
6.	Navigieren zum Dataflow-Fenster des Browsers zurück zu **df_Sales_ADLS**.
7.	Wählen Sie im linken Bereich den Bereich **Abfragen** aus, und geben Sie **STRG+V** ein (derzeit wird das Einfügen mit der rechten Maustaste nicht unterstützt). Wenn Sie ein MAC-Gerät verwenden, drücken Sie zum Einfügen bitte Cmd+V.

**Hinweis:** Wenn Sie in der Übungsumgebung arbeiten, wählen Sie die Auslassungspunkte oben rechts auf dem Bildschirm aus. Verwenden Sie den Schieberegler, um das **VM Native Clipboard zu
aktivieren**. Wählen Sie im Dialogfeld OK aus. Nachdem Sie die Abfragen eingefügt haben, können Sie diese Option deaktivieren.









