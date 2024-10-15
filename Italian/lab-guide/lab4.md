# Microsoft Fabric - Fabric Analyst in a Day - Lab 4

![]()

# Sommario

- Introduzione

- Flusso di dati Gen2

    - Attività 1: Copia di query SharePoint nel flusso di dati 

    - Attività 2: Creazione della connessione a SharePoint

    - Attività 3: Configurazione della destinazione dei dati per la query People 

    - Attività 4: Pubblicazione e ridenominazione del flusso di dati SharePoint

    - Attività 5: Copia di query di Snowflake nel flusso di dati

    - Attività 6: Creazione della connessione a Snowflake 

    - Attività 7: Configurazione della destinazione dei dati per le query Supplier e PO

    - Attività 8 - Ridenominazione e pubblicazione del flusso di dati Snowflake 

- Collegamento ad ADLS Gen2 

    - Attività 9: Come creare un collegamento a Dataverse

    - Attività 6: Creazione di un collegamento al lakehouse 

- Riferiment

# Introduzione

Nel nostro scenario, i dati sui fornitori si trovano in Snowflake, i dati sui clienti si trovano in Dataverse e i dati sui dipendenti si trovano in SharePoint. Tutte queste origini dati vengono aggiornate in momenti diversi. Per ridurre al minimo il numero di aggiornamenti dei dati dei flussi di dati, creeremo flussi di dati individuali per le origini dati Snowflake e SharePoint.

**Nota**: è supportata la presenza di più origini dati in un unico flusso di dati.

Il team IT ha già stabilito un collegamento a Dataverse e applicato le necessarie trasformazioni dei dati, eseguendone il mirroring nel file Power BI Desktop. Ha inserito questi dati nel lakehouse nell'area di lavoro di amministrazione e ha concesso l'accesso alle tabelle. Ora procederemo a creare un collegamento per il lakehouse creato dal team IT.

In questo lab si apprenderà quanto segue: 
- Come stabilire una connessione a SharePoint mediante Flusso di dati Gen2 e inserire dati in lakehouse.
- Come stabilire una connessione a Snowflake tramite Flusso di dati Gen2 e inserire dati in Lakehouse.
- Come inserire dati in un lakehouse condiviso.

# Flusso di dati Gen2

## Attività 1: Copia di query SharePoint nel flusso di dati

1. Torniamo all'area di lavoro di Fabric **FAIAD_\<nome utente>** creata nel Lab 2, Attività 9.

2. Selezionare l'icona **selettore esperienza Fabric in basso** a sinistra della schermata. Si apre la finestra di dialogo Esperienza Fabric

3. Selezionare **Data Factory** nella finestra di dialogo. Verrà visualizzata la **home page di Data Factory**.

    ![]()

4. Nella sezione dedicata agli elementi consigliati, selezionare **Flusso di dati Gen2.**

    ![]()

Verrà visualizzata la pagina **Flusso di dati**. L'interfaccia di Flusso di dati Gen2 è simile a Power Query in Power BI Desktop. Possiamo copiare le query da Power BI Desktop a Flusso di dati Gen2. Proviamo.

5. Se non è già stato fatto, aprire il file **FAIAD.pbix** che si trova nella cartella **Reports** sul desktop dell'ambiente lab. 

6. Nella barra multifunzione selezionare **Home -> Trasforma dati**. Si apre la finestra Power Query. Come si è notato nel lab precedente, le query nel pannello di sinistra sono organizzate per origine dati.

7. Dal pannello di sinistra **selezionare** la query **People** nella cartella SharepointData.

8. **Fare clic con il pulsante destro del mouse** e selezionare **Copia**.

    ![]()

9. Tornare alla schermata **Flusso di dati** nel browser.

10. Nel **riquadro Flusso di dati** premere **CTRL+V** (l'opzione Incolla del menu del pulsante destro non è attualmente supportata). Se si usa un dispositivo MAC, usare Cmd+V per incollare.

**Nota**: se si lavora in un ambiente lab, selezionare i puntini di sospensione in alto a destra della schermata. Usare il dispositivo di scorrimento per **abilitare VM Native Clipboard**. Nella finestra di dialogo selezionare OK. Dopo aver incollato le query è possibile disabilitare questa opzione.

Notare che la query viene incollata ed è disponibile nel pannello di sinistra. Poiché non abbiamo creato una connessione a SharePoint, compare un messaggio di avviso che chiede di configurare la connessione.

## Attività 2: Creazione della connessione a SharePoint

1. Selezionare **Configura connessione**.

    ![]()

2. Si apre la finestra di dialogo Connetti a origine dati. Assicurarsi che nel menu a discesa **Connessione** sia selezionato **Crea nuova connessione**.

3. Il **Tipo di autenticazione** dovrebbe essere **Account aziendale**.

4. Selezionare **Connetti**.

    **Nota**: l'accesso verrà eseguito usando le proprie credenziali. Saranno diverse rispetto allo screenshot qui sotto.

    ![]()

## Attività 3: Configurazione della destinazione dei dati per la query People

Viene stabilita la connessione ed è possibile visualizzare i dati nel pannello di anteprima. Esplorare i Passaggi applicati delle query. Ora dobbiamo inserire i dati di People in Lakehouse.

1. Selezionare la query **People**.

2. Nella barra multifunzione selezionare **Home -> Aggiungi destinazione dati -> Lakehouse**.

    ![]()

3. Si apre la finestra di dialogo Connetti alla destinazione dati. Dobbiamo creare una nuova connessione a Lakehouse. Con l'opzione **Crea nuova connessione** selezionata nel menu a discesa **Connessione** e **Tipo di autenticazione** impostato su **Account aziendale**, selezionare **Avanti**.

    ![]()

4. Si apre la finestra di dialogo Scegliere il target di destinazione. Assicurarsi che il pulsante di opzione **Nuova tabella** sia selezionato, poiché si sta creando una nuova tabella.

5. Vogliamo creare la tabella nel Lakehouse creato in precedenza. Nel pannello di sinistra andare a **Lakehouse -> FAIAD_\<nomeutente>**.

6. Selezionare **lh_FAIAD**

7. Lasciare il nome della tabella **People**

8. Selezionare **Avanti**.

    ![]()

9. Si apre la finestra di dialogo Scegli le impostazioni di destinazione. Assicurarsi che l'opzione "**Usa impostazioni automatiche**" sia **abilitata**. 

**Nota**: se si disabilitano le impostazioni automatiche, si potrà notare che sono disponibili opzioni per impostare il metodo di aggiornamento e opzioni dello schema. Dopo aver vagliato le possibilità offerte, assicurarsi che l'opzione "**Usa impostazioni automatiche**" sia **abilitata**. 

10. Selezionare **Salva impostazioni**.

    ![]()

## Attività 4: Pubblicazione e ridenominazione del flusso di dati SharePoint

1. Si apre nuovamente la **finestra di Power Query**. Nell'**angolo in basso a destra** notare che la Destinazione dati è impostata su **Lakehouse**.

2. Nell'angolo inferiore destro selezionare **Pubblica**.

    ![]()

    **Nota**: si tornerà all'**area di lavoro FAIAD_\<nome utente>**. La pubblicazione del flusso di dati potrebbe richiedere alcuni istanti. 

3. Stiamo lavorando in Dataflow 1. Rinominiamolo prima di continuare. Fare clic sui **puntini di sospensione (…)** accanto a Dataflow 1. Selezionare **Proprietà**.

    ![]()

4. Si apre la finestra di dialogo Proprietà flusso di dati. Cambiarne il **Nome** in **df_People_SharePoint**.

5. Nella casella di testo **Descrizione** aggiungere **Flusso di dati per inserire i dati di People da SharePoint in Lakehouse**.

6. Selezionare **Salva**.

    ![]()

Si tornerà all'area di lavoro **FAIAD_\<nome utente>**.

7. Selezionare **lh_FAIAD** per spostarsi nel lakehouse.

8. Accertarsi di essere nella vista Lakehouse (non nell'endpoint di Analisi SQL).

9. Notare la tabella **People** ora disponibile nel lakehouse.

**Nota**: se le tabelle appena create non sono visibili, selezionare i puntini di sospensione accanto a Tables e selezionare Aggiorna per aggiornare le tabelle.

Ora abbiamo inserito tutti i dati nel lakehouse. Nel prossimo lab pianificheremo l'aggiornamento del flusso di dati.

## Attività 5: Copia di query di Snowflake nel flusso di dati

1. Torniamo all'area di lavoro di Fabric **FAIAD_\<nome utente>**.

2. Nel menu in alto selezionare **Nuovo -> Flusso di dati Gen2**.

    ![]()

Verrà visualizzata la pagina **Flusso di dati**. Ora che abbiamo familiarità con Flusso di dati, procediamo con la copia delle query da Power BI Desktop a Flusso di dati.

3. Se non è già stato fatto, aprire il file **FAIAD.pbix** che si trova nella cartella **Reports** sul desktop dell'ambiente lab. 

4. Nella barra multifunzione selezionare **Home -> Trasforma dati**. Si apre la finestra Power Query. Come si è notato nel lab precedente, le query nel pannello di sinistra sono organizzate per origine dati.

5. Nel pannello di sinistra selezionare le seguenti query nella cartella SnowflakeData tenendo premuto il tasto **CTRL o MAIUSC**:
    
    a. SupplierCategories
    
    b. Suppliers
    
    c. Supplier
    
    d. PO
    
    e. PO Line Items

6. **Fare clic con il pulsante destro del mouse** e selezionare **Copia**.

    ![]()

7. Tornare al **browser**.

8. Nel **riquadro Flusso di dati** selezionare il **riquadro centrale** e premere **CTRL+V** (l'opzione Incolla del menu del pulsante destro non è attualmente supportata). Se si usa un dispositivo MAC, usare Cmd+V per incollare.

    **Nota**: se si lavora in un ambiente lab, selezionare i puntini di sospensione in alto a destra della schermata. Usare il dispositivo di scorrimento per **abilitare VM Native Clipboard**. Nella finestra di  dialogo selezionare OK. Dopo aver incollato le query è possibile disabilitare questa opzione.

    ![]()

## Attività 6: Creazione della connessione a Snowflake

Notare che le cinque query vengono incollate e sulla sinistra è visualizzato il pannello Query. Poiché non abbiamo creato una connessione a Snowflake, compare un messaggio di avviso che chiede di configurare la connessione.

1. Selezionare **Configura connessione**.

    ![]()

2. Si apre la finestra di dialogo Connetti a origine dati. Assicurarsi che nel menu a discesa **Connessione** sia selezionato **Crea nuova connessione**.

3. Il **Tipo di autenticazione** dovrebbe essere impostato su **Snowflake**.

4. Immettere **nome utente e password di Snowflake** disponibili nella scheda Variabili di ambiente (accanto alla scheda Guida al lab).

5. Selezionare **Connetti**.

    ![]()

Viene stabilita la connessione ed è possibile visualizzare i dati nel pannello di anteprima. Esplorare i Passaggi applicati delle query. In genere, la query Suppliers contiene i dettagli sui fornitori e SupplierCategories contiene le categorie di fornitori. Queste due tabelle vengono unite per creare la dimensione Supplier, con le colonne necessarie. Analogamente, PO Line Items viene unita con PO per creare il fatto PO. Ora dobbiamo inserire i dati di Supplier e PO in Lakehouse.

