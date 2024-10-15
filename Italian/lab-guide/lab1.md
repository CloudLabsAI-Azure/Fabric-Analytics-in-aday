

# Sommario
- Struttura del documento
  
- Scenario/Esposizione del problema
  
- Panoramica del report di Power BI Desktop
  
  - Attività 1 - Impostazione di Power BI Desktop nell'ambiente lab
    
  - Attività 2 - Analisi del report di Power BI Desktop
    
  - Attività 3 - Analisi delle query in Power Query
  
- Riferimenti

Struttura del documento

Il lab include i passaggi che l'utente deve seguire con gli screenshot associati che forniscono un aiuto 
visivo. In ogni screenshot vi sono sezioni evidenziate con riquadri arancioni che indicano le aree su 
cui l'utente deve concentrarsi.
Nota: alcuni screenshot potrebbero non essere aggiornati a causa dei continui aggiornamenti del 
prodotto.
Scenario/Esposizione del problema
Fabrikam, Inc. è un distributore di oggettistica all'ingrosso. Poiché Fabrikam è un grossista, i suoi clienti 
sono soprattutto aziende che rivendono ai consumatori. Fabrikam vende a rivenditori al dettaglio in 
tutti gli Stati Uniti, inclusi negozi specializzati, supermercati, negozi di informatica e di souvenir per 
turisti. Fabrikam vende anche ad altri grossisti attraverso una rete di agenti che promuovono i prodotti 
per conto di Fabrikam. Sebbene tutti i clienti di Fabrikam abbiano sede negli Stati Uniti, l'azienda 
desidera espandersi in altri paesi/aree geografiche.
In qualità di analista dei dati del team di vendita, si raccolgono, puliscono e interpretano set di dati 
per risolvere i problemi aziendali. Si compongono anche visualizzazioni come grafici e diagrammi, si 
scrivono report e li presentano ai decision-maker dell'organizzazione.
Per ottenere informazioni utili, si estraggono, puliscono e organizzano insieme dati provenienti da più 
sistemi. Si ottengono dati dalle seguenti origini:
• Dati di vendita: provengono dal sistema ERP e sono archiviati in un database ADLS Gen2.
Vengono aggiornati alle 12.00 ogni giorno.
• Dati sui fornitori: provengono da diversi fornitori e sono archiviati in un database Snowflake. 
Vengono aggiornati alle 00.00 ogni giorno.
• Dati sui clienti: provengono da Customer Insights e sono archiviati in Dataverse. I dati sono 
sempre aggiornati.
• Dati sui dipendenti: provengono dal sistema HR e sono archiviati in un file di esportazione in 
una cartella di SharePoint. Vengono aggiornati ogni mattina alle 9.00. 
Versione: 08.2024 Copyright 2024 Microsoft 4|Pagina 
Gestito da: Microsoft Corporation
Attualmente si sta creando un set di dati in Power BI Premium che estrae i dati dai sistemi di origine 
sopraelencati al fine di soddisfare le esigenze di reporting e fornire agli utenti finali possibilità di uso 
self-service. Si usa Power Query per aggiornare il modello. 
Si devono affrontare le seguenti problematiche:
• È necessario aggiornare il set di dati almeno tre volte al giorno per adattarsi ai diversi tempi 
di aggiornamento delle diverse origini dati.
• Gli aggiornamenti richiedono molto tempo in quanto è necessario eseguire un aggiornamento 
completo ogni volta per acquisire eventuali aggiornamenti dei sistemi di origine.
• Se si verificano errori in qualsiasi delle origini dati da cui si estraggono i dati, l'aggiornamento 
del set di dati si interrompe. Spesso il file dei dipendenti non viene caricato in tempo e ciò 
causa l'interruzione dell'aggiornamento del set di dati. 
• Eventuali modifiche al modello di dati richiedono molto tempo in quanto Power Query 
richiede molto tempo per l'aggiornamento delle anteprime, date le dimensioni elevate dei 
dati e le trasformazioni complesse. 
• È necessario un PC Windows per usare Power BI Desktop anche se lo standard aziendale è Mac.
Si è sentito parlare di Microsoft Fabric e si è deciso di provarlo per verificare se può risolvere queste 
problematiche.
Panoramica del report di Power BI Desktop
Prima di iniziare con Fabric, esaminiamo l'attuale report in Power BI Desktop per comprendere le 
trasformazioni e il modello.
Attività 1 - Impostazione di Power BI Desktop nell'ambiente lab
1. Aprire il file FAIAD.pbix contenuto nella cartella Reports sul Desktop dell'ambiente lab. Il file si 
aprirà in Power BI Desktop.
Versione: 08.2024 Copyright 2024 Microsoft 5|Pagina 
Gestito da: Microsoft Corporation
2. Si apre la finestra di dialogo Immettere l'indirizzo e-mail. Andare alla scheda Environment Details 
sul pannello di destra nell'ambiente lab.
3. Copiare il Nome utente e incollarlo nella casella di testo E-mail della finestra di dialogo.
4. Selezionare Continua.
5. Si apre la finestra di dialogo Accedi. Immettere nuovamente il Nome utente copiandolo nella 
scheda Dettagli ambiente.
6. Selezionare Avanti.
7. Nella finestra di dialogo successiva immettere le Credenziali e la Password copiandole dalla 
scheda Dettagli ambiente.
8. Selezionare Accedi.
9. Viene visualizzata la finestra di dialogo Rimani connesso a tutte le app. Selezionare OK.
Versione: 08.2024 Copyright 2024 Microsoft 6|Pagina 
Gestito da: Microsoft Corporation
10. Viene visualizzata la finestra di dialogo Operazione completata. Selezionare Fatto.
Si aprirà Power BI Desktop.
Attività 2 - Analisi del report di Power BI Desktop
Il report seguente analizza le vendite per Fabrikam. I KPI sono elencati in alto a sinistra nella pagina. Gli 
oggetti visivi rimanenti evidenziano le vendite nel tempo, per area, gruppo di prodotti e azienda rivenditrice. 
Versione: 08.2024 Copyright 2024 Microsoft 7|Pagina 
Gestito da: Microsoft Corporation
Nota: in questo corso di formazione ci concentreremo sull'acquisizione, la trasformazione e la modellazione 
dei dati mediante gli strumenti disponibili in Fabric. Non ci concentreremo sullo sviluppo di report né sullo 
spostamento al loro interno. Dedichiamo qualche minuto alla comprensione del report prima di procedere 
ai passaggi successivi.
1. Analizziamo i dati per area di vendita. Selezionare New England nel grafico a dispersione Sales 
Territory. In Sales over time notare che il rivenditore Tailspin Toys presenta più vendite di Wingtip 
Toys in New England. Se si considera l'istogramma % vendite rispetto all'anno precedente, si noterà 
che la crescita delle vendite di Wingtip Toys è stata bassa ed è calata di trimestre nello scorso anno. 
Dopo un leggero rialzo nel terzo trimestre è nuovamente calata nel quarto. 
2. Confrontiamo questi dati con l'area delle Montagne Rocciose. Selezionare Rocky Mountain nel 
grafico a dispersione Sales Territory. Dall'istogramma % vendite rispetto all'anno precedente 
risulta che le vendite per Wingtip Toys sono aumentate notevolmente nel quarto trimestre del 
2022 dopo essere state basse nei due trimestri precedenti.
Versione: 08.2024 Copyright 2024 Microsoft 8|Pagina 
Gestito da: Microsoft Corporation
3. Selezionare Rocky Mountain in Sales Territory per rimuovere il filtro.
4. Nel grafico a dispersione in basso al centro della schermata (ordini cliente rispetto alle vendite) 
selezionare l'outlier in alto a destra (4° quadrante). Notare che la percentuale di margine è il 52%, 
superiore alla media del 50%. Inoltre, la percentuale di vendite rispetto all'anno precedente è 
aumentata negli ultimi due trimestri del 2023.
5. Selezionare il rivenditore outlier nel grafico a dispersione per rimuovere il filtro.
6. Otteniamo i dettagli del prodotto per gruppo di prodotti e rivenditore. Nel grafico a barre Vendite 
per gruppo di prodotti e azienda rivenditrice fare clic con il pulsante destro del mouse sulla barra 
Packaging Materials per Tailspin Toys e nella finestra di dialogo selezionare Drill-through -> 
Product Detail.
Versione: 08.2024 Copyright 2024 Microsoft 9|Pagina 
Gestito da: Microsoft Corporation
Si passerà alla pagina che fornisce i dettagli del prodotto. Notare che sono anche presenti alcuni 
ordini futuri.
7. Dopo aver esaminato questa pagina, selezionare CTRL + freccia indietro in alto nella pagina per 
tornare al report vendite.
8. Se lo si desidera, analizzare ulteriormente il report, dopodiché esamineremo la vista modello. Nel 
pannello a sinistra selezionare l'icona della vista modello. Notare che vi sono due tabelle dei fatti 
Sales e PO. 
a. La granularità dei dati di Sales è per Date, Reseller, Product e People. Date, Reseller, 
Product e People si collegano a Sales.
b. La granularità dei dati di PO è per Date, Product e People. Date, Product e People si 
collegano a PO.
c. Abbiamo dati di Supplier per Product. Supplier si collega a Product.
d. Abbiamo dati località di Reseller per Geo. Geo si collega a Reseller.
e. Abbiamo informazioni di Customer per Reseller. Customer si collega a Reseller. 
Versione: 08.2024 Copyright 2024 Microsoft 10|Pagina 
Gestito da: Microsoft Corporation
Attività 3 - Analisi delle query in Power Query
1. Osserviamo Power Query per comprendere le origini dati. Nella barra multifunzione selezionare 
Home -> Trasforma dati.
2. Si apre la finestra Power Query. Nella barra multifunzione selezionare Home -> Impostazioni
origine dati. Scorrendo l'elenco si noterà che vi sono quattro origini dati, come indicato 
nell'esposizione del problema:
a. Snowflake
b. SharePoint
c. ADLS Gen2
d. Dataverse
3. Selezionare Chiudi per chiudere la finestra di dialogo Impostazioni origine dati.
Versione: 08.2024 Copyright 2024 Microsoft 11|Pagina 
Gestito da: Microsoft Corporation
4. Nel pannello Query a sinistra, notare che le query sono raggruppate per origine dati. 
5. Notare che la cartella DataverseData contiene dati sul cliente disponibili in quattro query 
diverse: BabyBoomer, GenX, GenY e GenZ. Queste quattro query vengono aggiunte per creare la 
query Customer.
6. È possibile immettere le credenziali per l'origine dati Dataverse immettendo Nome utente e 
Password disponibili nella scheda Variabili di ambiente (accanto alla guida al lab). Selezionare 
l'opzione dell'account Microsoft.
Versione: 08.2024 Copyright 2024 Microsoft 12|Pagina 
Gestito da: Microsoft Corporation
7. Per l'origine dati ADLS, usare l'opzione Chiave account e immettere la chiave di accesso 
dell'account di archiviazione ADLS, disponibile nella scheda Variabili di ambiente (accanto alla 
guida al lab).
8. Notare che la cartella ADLSData include più dimensioni: Geo, Product, Reseller e Date. Include 
anche il fatto Sales. 
a. La dimensione Geo è creata unendo i dati dalle query Cities, Countries e States. 
b. La dimensione Product è creata unendo i dati dalle query Product Groups e Product 
Item Group.
c. La dimensione Reseller è filtrata usando la query BuyingGroup.
d. Il fatto Sales è creato unendo le query InvoiceLineItems e Invoice.
9. Per l'origine dati Snowflake, usare il Nome utente Snowflake e la Password Snowflake disponibili 
nella scheda Variabili di ambiente (accanto alla guida al lab).
10. Notare che la cartella SnowflakeData include la dimensione Supplier e il fatto PO (ordine/spesa).
a. La dimensione Supplier è creata unendo le query Suppliers e SupplierCategories.
b. Il fatto PO è creato unendo le query PO e PO Line Items.
11. Per l'origine dati SharePoint, immettere il Nome utente e la Password disponibili nella scheda 
Variabili di ambiente (accanto alla guida al lab). Selezionare l'opzione dell'account Microsoft.
12. Notare che la cartella SharepointData include la dimensione People.
Versione: 08.2024 Copyright 2024 Microsoft 13|Pagina 
Gestito da: Microsoft Corporation
Ora conosciamo gli elementi con cui dobbiamo lavorare. Nel lab seguenti creeremo una query di 
Power Query analoga usando Flusso di dati Gen2 e un modello mediante Lakehouse.

