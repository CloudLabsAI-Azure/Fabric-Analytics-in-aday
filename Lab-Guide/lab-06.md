## Inhalt

- Einführung

- Lakehouse

   - Aufgabe 1: Daten mithilfe von SQL abfragen

   - Aufgabe 2: T-SQL-Ergebnis veranschaulichen	

   - Aufgabe 3: visuelle Abfrage erstellen	

   - Aufgabe 4: Abfrageergebnisse visualisieren	

   - Aufgabe 5: Beziehungen erstellen

   - Aufgabe 6: Measures erstellen	

   - Aufgabe 7: Fakultativer Abschnitt – Beziehungen erstellen	
   - Aufgabe 8: Fakultativer Abschnitt – Measures erstellen

- Referenzen	

Einführung
Wir haben Daten aus verschiedenen Datenquellen im Lakehouse erfasst. In dieser Übung arbeiten Sie mit dem Datenmodell. Üblicherweise werden Modellierungsarbeiten wie das Erstellen von Beziehungen, das Hinzufügen von Measures usw. in Power BI Desktop durchgeführt. Nun erfahren Sie, wie Sie diese Vorgänge im Dienst durchführen können.
Inhalt dieser Übung:
•	Lakehouse
•	SQL-Ansicht in Lakehouse
•	Datenmodellierung in Lakehouse

## Lakehouse

## Aufgabe 1: Daten mithilfe von SQL abfragen

1. Navigieren wir nun zurück zum Fabric-Arbeitsbereich **FAIAD_< username >**, den Sie in Übung 2, Aufgabe 9, erstellt haben.

2. Sie sehen drei Arten von lh_FAIAD – Lakehouse, Semantikmodell und SQL-Endpunkt. Lakehouse ist Ihnen schon aus einer früheren Übung bekannt. Um sich mit der SQL-Option zu beschäftigen, wählen Sie **lh_FAIAD SQL-Analyse-Endpunkt** aus. Sie werden zur SQL-Ansicht des Explorers weitergeleitet.

Wenn Sie sich die Daten vor der Erstellung eines Datenmodells genauer ansehen möchten, können Sie dies mit SQL tun. Betrachten wir jetzt zwei Möglichkeiten zur Nutzung von SQL, von denen die erste besonders für Entwickler geeignet ist, die zweite für Analysten.

Angenommen, Sie möchten mithilfe von SQL schnell die von einem Lieferanten verkauften Einheiten ermitteln. Dazu gibt es zwei Möglichkeiten: Sie schreiben eine SQL-Anweisung, oder Sie erstellen diese mit einem visuellen Element.
 
Beachten Sie, dass Sie links die Tabellen anzeigen können. Wenn Sie diese erweitern, sehen Sie die
Spalten der Tabelle. Außerdem lassen sich SQL-Ansichten, Funktionen und gespeicherten Prozeduren erstellen. Wenn Sie bereits Erfahrung mit SQL haben, probieren Sie diese Optionen gerne aus. Schreiben wir nun eine einfache SQL-Abfrage.

3. Wählen Sie im **Menü oben** die Option **Neue SQL-Abfrage** aus, oder klicken Sie **links unten** auf
**Abfrage**. Die Ansicht „SQL-Abfrage“ wird geöffnet.

4. Fügen Sie die unten **stehende SQL-Abfrage** in das **Abfragefenster** ein. Mit dieser Abfrage werden die Units by Supplierenname ermittelt. Dazu wird die Tabelle „Sales“ mit den Tabellen „Product“ und „Supplier" verknüpft.
```
    SELECT su.Supplier_Name, SUM(Quantity) as Units FROM 
    dbo.Sales s
    JOIN dbo.Product p on p.StockItemID = s.StockItemID 
    JOIN 
    dbo.Supplier su on su.SupplierID = p.SupplierID GROUP 
    BY su.Supplier_Name
```
5. Zeigen Sie die Ergebnisse mit **Ausführen** an.

6. Beachten Sie, dass die Abfrage mit der Option **Als Ansicht speichern** gespeichert werden kann.

7. Die Abfrage wird dann **links** im Bereich **Explorer** unter dem Abschnitt **Abfragen** unter **Meine Abfragen** als **SQL-Abfrage 1** gespeichert. So kann die Abfrage umbenannt und zur späteren Verwendung gespeichert werden. Es ist auch möglich, Abfragen anzuzeigen, die an Sie freigegeben wurden. Öffnen Sie dazu den Ordner **Freigegebene Abfragen**.

## Aufgabe 2: T-SQL-Ergebnis veranschaulichen

1. Das Ergebnis der Abfrage kann auch bildlich veranschaulicht werden. **Markieren Sie die Abfrage** im Abfragebereich, und wählen Sie erst den Bereich **Ergebnisse** und dann **Diese Daten erkunden** aus.

2. Das Dialogfeld **SQL-Abfrage erkunden** wird geöffnet. Erweitern Sie im Bereich **Daten** den Eintrag
**SQL-Abfrage 1**.

3. Wählen Sie die Felder **Supplier_Name** und **Units** aus. Es wird ein gruppiertes Balkendiagramm erstellt wird.

4. Ändern Sie unter Visualisierung die Art der Abbildung durch Auswahl des **gestapelten Säulendiagramms**.
 
5. **Erweitern Sie die Matrix**, um die Daten als Matrix anzuzeigen.

6. Wählen Sie **Speichern - > Als Bericht speichern** oben rechts auf dem Bildschirm aus.
 
 
7. Das Dialogfeld „Bericht speichern“ wird geöffnet. Geben Sie im Textfeld **Bericht benennen** den Text **Units by Supplier** ein.

8. Überprüfen Sie, dass der Zielarbeitsbereich Ihrem Fabric-Arbeitsbereich **FAIAD< Benutzername >**
entspricht.

9. Klicken Sie auf **Speichern**.

Sie gelangen zum vollständigen Bericht. Sie haben Optionen zum Formatieren der visuellen Elemente. Wir schauen uns diese Optionen in der nächsten Übung näher an.
 
10.	Klicken Sie links auf **lh_FAIAD**.




