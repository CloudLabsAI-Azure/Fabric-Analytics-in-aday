![](../Images/image7.1.png)

## Inhalt
Einführung
Power BI
  - Aufgabe 1: Bericht automatisch erstellen
  - Aufgabe 2: Hintergrund für einen neuen Bericht konfigurieren 
  - Aufgabe 3: Dem Bericht eine Kopfzeile hinzufügen 
  - Aufgabe 4: Dem Bericht KPIs hinzufügen
  - Aufgabe 5: Dem Bericht ein Liniendiagramm hinzufügen
  - Aufgabe 6: Den Bericht speichern
  - Aufgabe 7: Spalte „Year“ in der Tabelle „Date“ konfigurieren 
  - Aufgabe 8: Die Spalte „Short_Month_Name“ in der Tabelle „Date“ konfigurieren 
  - Aufgabe 9: Liniendiagramm formatieren 
  - Aufgabe 10: Neue Daten hinzufügen, um den Direct Lake-Modus zu simulieren 

Übungsumgebung bereinigen 

Referenzen 
## Einführung
Wir haben Daten aus verschiedenen Datenquellen in Lakehouse erfasst, eine Einführung in
Lakehouse erhalten, einen Aktualisierungsplan für die Datenquellen festgelegt und ein Datenmodell
erstellt. Jetzt erstellen wir einen Bericht.
Inhalt dieser Übung:
  - So erstellen Sie einen Bericht automatisch
  - So erstellen Sie einen Bericht von einem leeren Canvas ausgehend
  - So erkunden Sie den Direct Lake-Modus, in dem Daten automatisch aktualisiert werden

## Power BI
### Aufgabe 1: Bericht automatisch erstellen
Verwenden wir zunächst die Option „Bericht automatisch erstellen“. Und später in der Übung
werden wir den Bericht, den wir in Power BI haben, neu erstellen.
1. Wir navigieren zurück zum **Fabric-Arbeitsbereich**, den Sie in der vorherigen Übung erstellt haben.
2. Wählen Sie unten links das Symbol **Fabric-Funktionsbereichs-Auswahl** aus.
3. Das Dialogfeld „Fabric-Funktionsbereich“ wird geöffnet. Wählen Sie **Power BI** aus. Sie werden zur
**Power BI-Startseite** weitergeleitet.
4. Wählen Sie **Neuer Bericht** aus dem oberen Menü aus.
5. Sie werden zu **Erstellen Sie Ihren ersten Bericht** weitergeleitet. Dort sind Optionen verfügbar, um Daten manuell einzugeben und einen Bericht zu erstellen oder um ein veröffentlichtes semantisches Modell auszuwählen. In den vorherigen Übungen haben wir ein semantisches Modell erstellt. Lassen Sie uns das verwenden. Wählen Sie die Option **Veröffentlichtes Semantikmodell auswählen** aus.
6. Die Seite „Ein in Ihrem Bericht zu verwendendes DataSet auswählen“ wird geöffnet. Beachten
Sie, dass wir über vier Optionen verfügen. **Wählen Sie lh_FAIAD aus**:
a. **lh_FAIAD:** Dies ist das Lakehouse mit dem DataSet, den wir erstellt haben und für den
Bericht verwenden möchten.
b. **Units by Supplier:** Dies ist das DataSet, das wir mit T-SQL erstellt haben.
c. **DataflowsStagingWarehouse:** Dies ist das Staging Warehouse, das standardmäßig
erstellt wird. Wir haben es nicht verwendet, da wir keine Daten bereitgestellt haben.
d. **DataflowsStagingLakehouse:** Dies ist das Staging Lakehouse, das standardmäßig erstellt
wird. Wir haben es nicht verwendet, da wir keine Daten bereitgestellt haben.

7. Klicken Sie auf den **Pfeil neben der Schaltfläche „Bericht automatisch erstellen“**. Beachten Sie,
dass es zwei Optionen gibt: „Bericht automatisch erstellen“ und „Leeren **Bericht erstellen“.
Versuchen** wir es mit der automatischen Erstellung. Wählen Sie daher Bericht automatisch
erstellen aus.
8. Power BI beginnt mit der automatischen Erstellung des Berichts. Beachten Sie, dass bei
entsprechender Auswahl eine Option für die Vorauswahl verschiedener Daten vorhanden ist.
Sobald der Bericht fertig ist, wird oben rechts auf dem Bildschirm ein Dialogfeld angezeigt.
Wählen Sie **View report now** aus.

**Prüfpunkt:** Sie erhalten einen Bericht, der wie im folgenden Screenshot aussieht. Es gibt einige KPIs
und einige Trendvisualisierungen. Dies ist ein guter Ausgangspunkt, wenn Sie ein neues Modell
analysieren und sofort starten müssen.

**Hinweis:** Im oberen Menü haben Sie die Möglichkeit, den Bericht zu bearbeiten oder einige der
Daten als Tabellen anzuzeigen. Sehen Sie sich diese Optionen doch einmal genauer an.
9. Speichern wir diesen Bericht. Wählen Sie im oberen Menü **Speichern** aus.
10. Das Dialogfeld „Bericht speichern“ wird geöffnet. Geben Sie dem Bericht den Namen
**rpt_Sales_Auto_Report**.
**Hinweis:** Wir stellen dem Berichtsnamen das Präfix „rpt“ voran, was für „Bericht“ steht.

11. Stellen Sie sicher, dass der Bericht in Ihrem Arbeitsbereich **FAIAD_<Benutzername>** gespeichert wird.
12. Wählen Sie **Speichern** aus.
**Hinweis:** Der automatisch erstellte Bericht kann für Sie anders aussehen, da er „automatisch erstellt“
wird. Dies hängt auch von den Beziehungen und Kennzahlen ab, die Sie in der vorangegangenen
Übung (Übung 6) erstellt haben.
Der Screenshot oben zeigt, wie der automatisch erstellte Bericht aussehen **könnte**, wenn Sie alle
Beziehungen und Kennzahlen einschließlich der optionalen Beziehungen (Übung 6) erstellt haben.
Der Screenshot unten zeigt, wie der automatisch erstellte Bericht aussehen **könnte**, wenn Sie die
Erstellung der optionalen Beziehungen und Kennzahlen (Übung 6) übersprungen haben.
### Aufgabe 2: Hintergrund für einen neuen Bericht konfigurieren
Lassen Sie uns einen neuen Bericht mit einer leeren Canvas erstellen.
1. Wählen Sie im **linken Bereich** den Namen Ihres Arbeitsbereichs, **FAIAD_<Benutzername>**, aus,
um zum Arbeitsbereich zu gelangen.
2. Wählen Sie im oberen Menü **Neu -> Bericht** aus. Sie werden zur Seite „Erstellen Sie Ihren ersten
Bericht” weitergeleitet.
3. Wählen Sie **Veröffentlichtes Semantikmodell auswählen** aus, damit wir das von uns erstellte
Modell auswählen können.
4. Das Dialogfeld „Ein in Ihrem Bericht zu verwendendes Semantikmodell auswählen“ wird
geöffnet. Wählen Sie **lh_FAIAD** aus.
5. Klicken Sie auf den **Pfeil neben der Schaltfläche „Bericht automatisch erstellen“**. Wählen Sie
**Leeren Bericht erstellen** aus.
6. Öffnen Sie **FAIAD.pbix** im Ordner **C:\FAIAD\Reports** in Ihrer Übungsumgebung, falls dies noch
nicht erfolgt ist.
Wir werden diesen Bericht als Referenz verwenden. Wir fügen zunächst den Canvashintergrund
hinzu. Wir erstellen die Berichtskopfzeile, fügen einige KPIs hinzu und erstellen das Liniendiagramm
„Verkäufe im Laufe der Zeit“. Aus Zeitgründen und davon ausgehend, dass Sie bereits Erfahrung mit
der Erstellung von Visuals Power BI Desktop haben, werden wir nicht alle Visuals erstellen.
7. Navigieren Sie zurück zum **Power BI-Canvas** in Ihrem Browser.
8. Wählen Sie im Visualisierungsbereich das **Symbol** für die **Formatseite** aus.
9. Erweitern Sie den **Abschnitt „Canvas-Hintergrund“**.
10. Wählen Sie **Durchsuchen** über die Option **Bild** aus. Das Dialogfeld „Datei-Explorer“ wird geöffnet.
11. Navigieren Sie zum Ordner **C:\FAIAD\Reports** in Ihrer Übungsumgebung.
12. Wählen Sie **Summary Background.png** aus.
13. Wählen Sie im Dropdownmenü **Bild anpassen** den Eintrag **Anpassen** aus.
14. Legen Sie die Transparenz auf **0 %** fest.
### Aufgabe 3: Dem Bericht eine Kopfzeile hinzufügen
1. Wir fügen nun die Kopfzeile am oberen Rand hinzu. Wählen Sie im **Menü** die Option **Textfeld** aus.
2. Geben Sie **Fabrikam Company** als erste Zeile in das Textfeld ein.
3. Geben Sie als zweite Zeile **Sales Report** in das Textfeld ein.
4. Markieren Sie **Fabrikam Company**, und legen Sie **Schriftart** auf **Segoe UI** und **Schriftgröße** auf **18**,
**Fett** fest.
5. Markieren Sie **Sales Report**, und legen Sie **Schriftart** auf **Segoe UI** und **Schriftgröße** auf **14** fest.
6. Erweitern Sie bei **ausgewähltem Textfeld** im Bereich „Textfeldformat“ rechts die Option **Effekte**.
7. Verwenden Sie den Schieberegler **Hintergrund**, um ihn auf **Aus** festzulegen.
8. Passen Sie die Größe des **Textfelds so an, dass es in den oberen Rand passt**.
### Aufgabe 4: Dem Bericht KPIs hinzufügen
1. Fügen wir nun Verkauf-KPI hinzu. Wählen Sie den **Leerraum** im Canvas aus, um den Fokus vom
Textfeld zu entfernen.
2. Wählen Sie im **Abschnitt Visualisierungen** die Option **Mehrzeiliges Kartenvisual** aus.
3. Erweitern Sie im **Abschnitt „Daten“** die **Tabelle Sales**.
4. Wählen Sie **Kennzahl „Sales“** aus.
5. Wenn das **mehrzeilige Kartenvisual ausgewählt ist**, wählen Sie das **Symbol „Visual formatieren“**
im Abschnitt „Visualisierungen“ aus.
6. Erweitern Sie den Abschnitt **Kategoriebeschriftungen** aus.
7. Erhöhen Sie die **Schriftgröße** auf **14**.
8. Wählen Sie das **Dropdownmenü „Farbe“** aus. Das Dialogfeld „Farbpalette“ wird geöffnet.
9. Legen Sie den HEX-Wert auf **#004753** fest.
10. Erweitern Sie den Abschnitt **Karten**.
11. Verwenden Sie den Schieberegler **Akzentleiste**, um ihn **auf** Aus festzulegen.
12. Wählen Sie im Visualisierungsbereich **Allgemein** aus.
13. Erweitern Sie den **Abschnitt „Effekte“**.
14. Verwenden Sie den Schieberegler **Hintergrund**, um ihn auf **Aus** festzulegen.
15. Ändern Sie die Größe des **Visuals**, und verschieben Sie es in das **linke Feld, wie im Screenshot
dargestellt.**
16. Fügen wir nun einen weiteren KPI hinzu. Wählen Sie die soeben erstellte **mehrzeilige Sales-Karte**
aus. **Kopieren Sie** das Visual, indem Sie **STRG+C** auf Ihrer Tastatur auswählen.
17. **Fügen Sie** das Visual ein, indem Sie **STRG+V** auf Ihrer Tastatur auswählen. Beachten Sie, dass das
Visual in das Canvas eingefügt wird.
18. Wenn das **neue Visual hervorgehoben ist**, entfernen Sie im Abschnitt **Visualisierungsbereich ->
Visual erstellen -> Felder** die Kennzahl **Sales**.
19. Erweitern Sie im Abschnitt **Daten** die Tabelle **Sales**, und wählen Sie die Kennzahl **Units** aus.
20. Ändern Sie die Größe des **Visuals** und **platzieren Sie es im Feld unter dem Sales-Visual**.
### Aufgabe 5: Dem Bericht ein Liniendiagramm hinzufügen
Lassen Sie uns ein Liniendiagramm erstellen, um Sales im Zeitverlauf nach Reseller Company zu
visualisieren.
1. Wählen Sie den **Leerraum** im Canvas aus, um den Fokus vom mehrzeiligen Kartenvisual zu
entfernen.
2. Wählen Sie im **Abschnitt Visualisierungen** die Option **Liniendiagramm** aus.
3. Erweitern Sie im **Abschnitt „Daten“** die Tabelle **Date**.
4. Wählen Sie das Feld **Year** aus. Beachten Sie, dass „Year“ standardmäßig summiert und der Y-
Achse hinzugefügt wird. Lassen Sie uns dies korrigieren.
### Aufgabe 6: Den Bericht speichern
Speichern wir den Bericht, bevor wir ihn verlassen, um Änderungen am Modell vorzunehmen.
1. Wählen Sie im Menü **Datei -> Speichern** aus.
2. Das Dialogfeld „Bericht speichern“ wird geöffnet. Geben Sie dem Bericht den Namen
**rpt_Sales_Report**.

**Hinweis:** Wir stellen dem Berichtsnamen das Präfix „rpt“ voran, was für „Bericht“ steht.

3. Stellen Sie sicher, dass der Bericht im Arbeitsbereich **FAIAD_<Benutzername>** gespeichert wird.
4. Wählen Sie **Speichern** aus.
### Aufgabe 7: Spalte „Year“ in der Tabelle „Date“ konfigurieren
1. Wählen Sie in der **linken Menüleiste lh_FAIAD** aus, um zum Lakehouse zu navigieren.
2. Erweitern Sie im linken Explorer-Bereich **lhFAIAD -> Schemas -> dbo -> Tables -> Date.**
3. Wählen Sie die Spalte **Year** aus.
4. Erweitern Sie im Bereich **Eigenschaften** rechts den Abschnitt **Erweitert**.
5. Wählen Sie aus der Dropdownliste **Zusammenfassen nach** den Eintrag **Keine** aus.
6. Kehren Sie zum Bericht zurück, indem Sie in der linken Menüleiste **rpt_Sales_Report** auswählen.
7. Wählen Sie im oberen Menü **Bearbeiten** aus.
8. Wählen Sie im oberen Menü **Aktualisieren** aus. Beachten Sie, dass „Year“ im Datenbereich kein
Summierungsfeld ist.
9. Wenn das **Visual „Liniendiagramm“ ausgewählt ist, entfernen Sie „Sum of Year“** von der Y-Achse.
10. Wählen Sie das Feld **Year** aus, sodass es der **X-Achse** hinzugefügt wird.
11. Erweitern Sie die Tabelle **Sales**, und wählen Sie die **Kennzahl „Sales“** aus.
### Aufgabe 8: Die Spalte „Short_Month_Name“ in der Tabelle „Date“ konfigurieren
1. Fügen wir diesem Diagramm „Monat“ hinzu. Ziehen Sie das Feld **Short_Month_Name** unter **Year**
aus der Tabelle „Date“ in die **X-Achse**. Beachten Sie dass das Visual nach „Sales“ sortiert ist. Nun
sortieren wir es nach Short_Month_Name.
2. Wählen Sie die **Auslassungspunkte (…)** oben rechts im Visual aus.
3. Wählen Sie **Sortierachse -> Year Short_Month_Name** aus.
4. Wählen Sie die **Auslassungspunkte (…)** oben rechts im Visual aus.
5. Wählen Sie **Sortierachse -> Aufsteigend sortieren** aus.