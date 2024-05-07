##Inhalt
- Einführung	
- Dataflow Gen2	
  - Aufgabe 1: Geplante Aktualisierung für den Verkaufs-Dataflow konfigurieren	
  - Aufgabe 2: Geplante Aktualisierung für den Lieferanten- und Kunden-Dataflow konfigurieren	
- Datenpipeline	
  - Aufgabe 3: Datenpipeline erstellen	
  - Aufgabe 4: Einfache Datenpipeline erstellen	
  - Aufgabe 5: Neue Datenpipeline erstellen	
  - Aufgabe 6: Bis-Aktivität erstellen	
  - Aufgabe 7: Variablen erstellen	
  - Aufgabe 8: Bis-Aktivität konfigurieren	
  - Aufgabe 9: Dataflow-Aktivität konfigurieren	
  - Aufgabe 10: Erste Aktivität „Variable festlegen“ konfigurieren	
  - Aufgabe 11: Zweite Aktivität „Variable festlegen“ konfigurieren	
  - Aufgabe 12: Dritte Aktivität „Variable festlegen“ konfigurieren	
  - Aufgabe 13: Wait-Aktivität konfigurieren	
  - Aufgabe 14: Geplante Aktualisierung für die Datenpipeline konfigurieren	
- Referenzen	

##Einführung
Wir haben Daten aus verschiedenen Datenquellen in Lakehouse erfasst. In dieser Übung richten Sie einen Aktualisierungszeitplan für die Datenquellen ein. Zusammenfassung der Anforderung:

- **Verkaufsdaten**: Diese werden in ADLS täglich mittags bzw. um 12:00 Uhr aktualisiert.

- **Lieferantendaten**: Diese werden in Snowflake täglich um Mitternacht/00:00 Uhr aktualisiert.
- **Kundendaten**: Diese sind in Dataverse immer auf dem neuesten Stand. Wir müssen diese
viermal täglich aktualisieren, um Mitternacht bzw. 00:00 Uhr, um 6:00 Uhr, mittags bzw. um 12:00 Uhr und um 18:00 Uhr.

- **Mitarbeiterdaten**: Diese werden in SharePoint täglich um 9:00 Uhr aktualisiert. Wir haben jedoch festgestellt, dass es manchmal zu einer Verzögerung von 5 bis 15 Minuten kommt. Wir müssen einen Aktualisierungsplan erstellen, um dies zu berücksichtigen.

Inhalt dieser Übung:

    - So konfigurieren Sie eine geplante Aktualisierung von Dataflow Gen2

    - So erstellen Sie eine Datenpipeline

    - So konfigurieren Sie eine geplante Aktualisierung einer Datenpipeline

   ##Dataflow Gen2
Aufgabe 1: Geplante Aktualisierung für den Verkaufs-Dataflow konfigurieren

Beginnen wir damit, eine geplante Aktualisierung des Verkaufs-Dataflows zu konfigurieren.

1.	Navigieren wir nun zurück zum Fabric-Arbeitsbereich **FAIAD_<username>**, den Sie in Übung 2, Aufgabe 9, erstellt haben.

2.	Alle von Ihnen erstellten Artefakte werden hier aufgelistet. Geben Sie rechts im Bildschirm **df** in das **Suchfeld** ein. Dadurch werden die Artefakte nach Dataflows gefiltert.

3.	Zeigen Sie mit der Maus auf die Zeile **df_Sales_ADLS**. Beachten Sie, dass die vertrauten Symbole
**Aktualisieren** und **Aktualisierung planen** verfügbar sind. Klicken Sie auf die **Auslassungspunkte (...).**
 
 4.	Beachten Sie, dass die Optionen „Löschen“, „Bearbeiten“ und „Dataflow exportieren“ vorhanden sind. Wir können Eigenschaften verwenden, um den Namen und die Beschreibung des Dataflows zu aktualisieren. Wir sehen uns den Aktualisierungsverlauf in Kürze an. Wählen Sie **Einstellungen** aus.

**Hinweis**: Die Seite „Einstellungen“ wird geöffnet. Im linken Bereich sind alle Dataflows aufgelistet.

5.	Wählen Sie im mittleren Bereich den Link **Verlauf aktualisieren** aus.

6.	Das Dialogfeld „Verlauf aktualisieren“ wird geöffnet. Es werden Ihnen einige Aktualisierungen aufgelistet . Hierbei handelt es sich um die Aktualisierungen, die bei der Veröffentlichung des Dataflows erfolgt sind. Wählen Sie den Link **Startzeit** aus.

    **Hinweis**: Die Startzeit ist für Sie unterschiedlich.

     Der Detailbildschirm wird geöffnet. Hier erhalten Sie Details zur Aktualisierung sowie eine Liste mit Start-, Endzeit und Dauer. Außerdem werden die aktualisierten Tabellen/Aktivitäten aufgelistet. Falls ein Fehler auftritt, können Sie auf den Namen der Tabelle/Aktivität klicken, um mehr zu erfahren.

 7. wir navigieren von dieser Seite weg, indem wir auf das **X** in der oberen rechten Ecke klicken. Sie werden zur **Seite„Dataflow-Einstellungen“** weitergeleitet.

8.	Erweitern Sie unter „Gateway-Verbindung“ **Datenquellen-Anmeldeinformationen**. Es wird eine Liste der im Dataflow verwendeten Verbindungen angezeigt. In diesem Fall „Lakehouse“ und
„ADLS“.
      
      a.  Lakehouse: Dies ist die Verbindung zum Erfassen von Daten aus Dataflow.

      b.  ADLS: Dies ist die Verbindung zu den ADLS-Quelldaten.
9.	Erweitern Sie **Aktualisieren**.
10.	Legen Sie den Schieberegler für **Aktualisierungszeitplan** auf **Ein** fest.
11.	Legen Sie das **Dropdownmenü Aktualisierungshäufigkeit** auf **Täglich** fest. Beachten Sie, dass Sie auch die Option „Wöchentlich“ auswählen können.
 
12.	Legen Sie die **Zeitzone** auf Ihre bevorzugte Zeitzone fest.

    **Hinweis**: Da es sich um eine Übungsumgebung handelt, können Sie die Zeitzone auf Ihre bevorzugte Zeitzone festlegen. In einem realen Szenario legen Sie die Zeitzone basierend auf Ihrem/Speicherort der Datenquelle fest.

13.	Klicken Sie auf den Link **Andere Uhrzeit hinzufügen**. Hinweis: Die Option **Uhrzeit** wird angezeigt.
14.	Legen Sie die **Uhrzeit** auf **Mittag** fest. Beachten Sie, dass Sie die Aktualisierung zu jeder vollen oder halben Stunde einstellen können.
15.	Wählen Sie **Übernehmen** aus, um diese Einstellung zu speichern.

    **Hinweis**: Durch Klicken auf den Link „Andere Uhrzeit hinzufügen“ können Sie mehrere Aktualisierungszeiten hinzufügen.Sie können auch Fehlerbenachrichtigungen an den Besitzer des Dataflows und an andere Kontakte senden.

##Aufgabe 2: Geplante Aktualisierung für den Lieferanten- und Kunden-Dataflow konfigurieren
1.	Wählen Sie im linken Bereich **df_Supplier_Snowflake** aus.
2.	Konfigurieren Sie den Aktualisierungszeitplan, sodass die Aktualisierung **täglich um Mitternacht/00:00 Uhr** durchgeführt wird.
3.	Wählen Sie **Übernehmen** aus, um diese Einstellung zu speichern.

4.	Wählen Sie im linken Bereich **df_Customer_Dataverse** aus.
5.	Konfigurieren Sie den Aktualisierungszeitplan, sodass die Aktualisierung viermal täglich erfolgt:
**um Mitternacht bzw. um 00:00 Uhr, um 6:00 Uhr, mittags bzw. um 12:00 Uhr und um 18 Uhr.**
6.	Wählen Sie **Übernehmen** aus, um diese Einstellung zu speichern.

    Wie bereits erwähnt, müssen wir eine benutzerdefinierte Logik erstellen, um das Szenario zu handhaben, in dem die Mitarbeiterdatei in SharePoint nicht rechtzeitig gesendet wird. Wir verwenden die Datenpipeline, um dieses Problem zu beheben.


#Datenpipeline
##Aufgabe 3: Datenpipeline erstellen
1.	Wählen Sie unten links auf dem Bildschirm das Symbol **Fabric-Funktionsbereichs-Auswahl** aus.
2.	Das Dialogfeld Microsoft Fabric wird geöffnet. Wählen Sie **Data Factory** aus. Sie navigieren zur Data Factory-Startseite.
 
3.	Wählen Sie im oberen Bereich **Datenpipeline** aus, um eine neue Pipeline zu erstellen.
4.	Das Dialogfeld „Neue Pipeline“ wird geöffnet. Geben Sie der Pipeline den Namen**pl_Refresh_People_SharePoint**.
5.	Wählen Sie **Erstellen** aus.

    Sie werden zur **Seite „Datenpipeline“** weitergeleitet. Wenn Sie bereits mit Azure Data Factory gearbeitet haben, sind Sie mit diesem Bildschirm vertraut. Verschaffen wir uns einen kurzen Überblick über das Layout.
 
    Sie befinden sich auf dem **Startbildschirm**. Im oberen Menü finden Sie Optionen zum Hinzufügen häufig verwendeter Aktivitäten: „Überprüfen“, „Ausführen“ und „Ausführungsverlauf anzeigen“. Im mittleren Bereich finden Sie ebenfalls Optionen zum schnellen Erstellen der Pipeline.

6.	Wählen Sie im oberen Menü die Option **Aktivitäten aus**. Das Menü enthält nun eine Liste mit häufig verwendeten Aktivitäten.
7.	Wählen Sie rechts im Menü die **Auslassungspunkte (…)** aus, um alle anderen verfügbaren Aktivitäten anzuzeigen. Wir werden einige dieser Aktivitäten in der Übung verwenden.

8.	Klicken Sie im oberen Menü auf **Ausführen**. Es werden Optionen zum Ausführen und Planen der Pipeline angezeigt. Hier finden Sie auch die Option zum Anzeigen des Ausführungsverlaufs mithilfe von „Ausführungsverlauf anzeigen“.

9.	Wählen Sie im oberen Menü die Option **Anzeigen** aus. Hier finden Sie Optionen zum Anzeigen des Codes im JSON-Format. Außerdem sind Optionen zum Formatieren der Aktivitäten verfügbar.

     **Hinweis**: Wenn Sie am Ende der Übung über einen JSON-Hintergrund verfügen, können Sie auch„JSON-Code anzeigen“ auswählen. Hier sehen Sie, dass die gesamte Orchestrierung, die Sie über die Entwurfsansicht durchführen, auch in JSON geschrieben werden kann.

##Aufgabe 4: Einfache Datenpipeline erstellen
    Beginnen wir mit der Erstellung der Pipeline. Wir benötigen eine Aktivität, um den Dataflow zu aktualisieren. Lassen Sie uns nach einer Aktivität suchen, die wir verwenden können.

1.	Wählen Sie im oberen Menü **Aktivitäten -> Dataflow** aus. Die Dataflow-Aktivität wird dem mittleren Designbereich hinzugefügt. Beachten Sie, dass der untere Bereich jetztKonfigurationsoptionen der Dataflow-Aktivität enthält.

2.	Wir werden die Aktivität so konfigurieren, dass sie eine Verbindung zur df_People_SharePoint- Aktivität herstellt. Wählen Sie im  **unteren Bereich** die Option  **Einstellungen** aus.

3.	Stellen Sie sicher, dass  **Arbeitsbereich** auf Ihren Fabric-Arbeitsbereich, **FAIAD_<Benutzername>**, festgelegt ist.

4.	Wählen Sie im **Dropdownmenü „Dataflow“** die Option **df_People_SharePoint** aus. Wenn diese Dataflow-Aktivität ausgeführt wird, erfolgt eine Aktualisierung von df_People_SharePoint. Das war doch einfach, oder? ●¨v

     **Hinweis**: Die Benachrichtigungsoption ist derzeit ausgegraut. Diese Funktion wird in Kürze aktiviert.
     
     Sie können Benachrichtigungen konfigurieren, die Sie darüber informieren, ob diese Aktivität erfolgreich war oder nicht.

    In unserem Szenario werden Mitarbeiterdaten nicht planmäßig aktualisiert. Manchmal kommt es zu einer Verzögerung. Sehen wir uns an, ob wir dies berücksichtigen können.

5.	Wählen Sie im **unteren Bereich** die Option **Allgemein** aus. Wir geben der Aktivität einen Namen und eine Beschreibung.

6.	Geben Sie im Feld **Name dfactivity_People_SharePoint** ein.

7.	Geben Sie im Feld **Beschreibung die Dataflow-Aktivität ein, um den df_People_Sharepoint- Dataflow zu aktualisieren**.

8.	Beachten Sie, dass eine Option zum Deaktivieren einer Aktivität vorhanden ist. Diese Funktion ist beim Testen oder Debuggen hilfreich. Behalten Sie die Einstellung **Aktiviert** bei.
 
9.	Es ist eine Option zum Festlegen eines **Timeouts** verfügbar. Lassen wir den **Standardwert**
unverändert, damit dem Dataflow genügend Zeit für die Aktualisierung zur Verfügung steht.

**Hinweis:** Wenn die Daten nicht planmäßig verfügbar sind, legen wir die Aktivität so fest, dass sie
dreimal alle 10 Minuten erneut ausgeführt wird. Wenn der dritte Versuch fehlschlägt, wird ein Fehler gemeldet.
10.	Legen Sie Wiederholen auf 3 fest.
11.	Erweitern Sie den Abschnitt Erweitert.
12.	Legen Sie Wiederholungsintervall (Sek.) auf 600 fest.
13.	Wählen Sie im Menü Startseite -> Symbol „Speichern“ aus, um die Pipeline zu speichern.

Beachten Sie, welchen Vorteil die Verwendung der Datenpipeline im Vergleich zur Festlegung des Dataflows auf eine geplante Aktualisierung bietet (wie es schon bei früheren Dataflows erfolgt ist):
•	Die Pipeline bietet die Möglichkeit der mehrmaligen Wiederholung, bevor die Aktualisierung fehlschlägt.
•	Die Pipeline ermöglicht eine Aktualisierung innerhalb von Sekunden, während beim Dataflow alle 30 Minuten eine geplante Aktualisierung erfolgt.










