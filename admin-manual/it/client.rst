======
Client
======

|product| client è una `Web Application <http://it.wikipedia.org/wiki/Applicazione_web>`__ che consente la visualizzazione ed il controllo completo in tempo reale dell'intero sistema telefonico attraverso una semplice e intuitiva interfaccia web. 

Requisiti
=========

Sono supportati i browser Google Chrome e Mozilla Firefox (:doc:`firefox`).

Prima configurazione
====================

 .. note:: E' necessario che tutti i client risolvano correttamente l'FQDN del server.

|product| è raggiungibile all'indirizzo:

::

 https://_server_/cti

Usare le proprie credenziali di sistema per effettuare il login.

Funzionalità di base
====================

Gestione telefonate
-------------------

È sufficiente inserire il numero da chiamare nell'apposita casella presente
nella parte superiore della pagina e confermare cliccando sull'icona
relativa a forma di cornetta telefonica che appare subito sotto. Se il testo
inserito è un numero di telefono valido, è anche possibile far partire la
telefonata direttamente premendo il tasto invio.

Quando si riceve una telefonata appare un popup di notifica che riporta le
informazioni sul chiamante.


.. note:: 

   Le informazioni mostrate nel popup vengono estrapolate dalla rubrica |product| e da quella centralizzata secondo il seguente ordine:

   1. contatto privato della rubrica |product| (solo il creatore del contatto vedrà tali informazioni)
   2. contatto presente nella rubrica centralizzata
   3. primo contatto pubblico trovato nelle rubrica |product|

Alla ricezione/esecuzione di una telefonata compare il :dfn:`box di gestione chiamata` in alto, che abilita l'utente all'esecuzione delle seguenti operazioni:

**redirezione**
    vengono proposte destinazioni differenti.

**hangup**
    chiusura della telefonata.

**parcheggio**
    libera il telefono inserendo la chiamata corrente in un parcheggio.

**registrazione**
    avvia e mette in pausa la registrazione della telefonata in corso.

**crea nota**
    possibilità di creare una nota/POST-IT che potrà essere consultata in seguito.

**apertura di un URL**
    l'URL è parametrizzabile con i dati del chiamante


Stato dell'interno
------------------

Nella parte superiore dell'applicazione sono presenti due icone che
consentono l'attivazione/disattivazione delle seguenti funzionalità:

**non disturbare (DND)**
    abilita il DND su tutti gli interni telefonici associati all'utente

    configura la presence CTI dell'utente come :dfn:`occupato`

    configura lo stato dell'account jabber associato all'utente come *occupato*

**inoltro di chiamata incondizionato verso la casella vocale associata all'utente**
    qualsiasi chiamata in ingresso verrà dirottata verso la casella vocale selezionata

**inoltro di chiamata incondizionato verso il numero cellulare specificato associato all'utente**
    qualsiasi chiamata in ingresso verrà dirottata verso il numero cellulare selezionato

**inoltro di chiamata incondizionato verso il numero inserito manualmente**
    qualsiasi chiamata in ingresso verrà dirottata verso il numero telefonico inserito

Se l'utente è membro statico/dinamico di una coda, sarà presente una terza icona
che consente:

**logon/logout dalle code in cui è membro dinamico**
    l'utente entra/esce da tutte le code in cui è membro dinamico

**pause/resume dalle code a cui appartiene**
    l'utente si mette in pausa o esce dal medesimo stato, su tutte le code in cui è correntemente loggato

Inviare SMS
-----------

È sufficiente inserire un numero di cellulare valido nell'apposita
casella in alto, che attiva il pulsante d'invio. Viene quindi
visualizzata la finestra in cui inserire il testo del messaggio.


Ricerca contatti
----------------

Attraverso la casella presente nella parte superiore è possibile
effettuare la ricerca di qualsiasi contatto presente nelle rubriche.

Le sorgenti dati in cui viene effettuata la ricerca sono:

- `Rubrica Centralizzata <http://nethserver.docs.nethesis.it/it/latest/phonebook-mysql.html>`_
- Rubrica |product|

Il click sul nome di un contatto mostrato nei risultati, visualizza la
relativa scheda cliente in base al numero telefonico del lavoro (campo
*workphone* del database *phonebook*). Questo comportamento è il default, ma è
personalizzabile tramite la voce :dfn:`"Cerca scheda cliente su"` presente
nel servizio `Configurazione`_.

Rubrica |product|
-----------------

È possibile creare dei propri contatti che vengono utilizzati da |product|
per la `ricerca contatti`_, per
visualizzare le informazioni del chiamante nel popup e per popolare la lista
degli `speed dial`_. Per ogni contatto creato è possibile scegliere tre tipologie
di privacy:

-  **privata:** sono contatti personali dell'utente che è l'unico a
   poterli vedere
-  **pubblica:** sono contatti visibili a tutti e quindi vengono
   mostrati nei risultati della ricerca in rubrica
-  **speed dial:** sono contatti privati dell'utente e vengono mostrati
   nella lista degli speed dial

Solo il creatore del contatto ha il diritto di modificarlo/eliminarlo e
lo può fare tramite il servizio di ricerca. Per creare un nuovo contatto
è sufficiente cliccare il pulsante "+" presente nella lista
degli speed dial oppure scrivere il nome da inserire nel campo presente
nella barra superiore e cliccare il pulsante "+" che appare subito sotto.

Per visualizzare i contatti della rubrica |product| anche nel telefono
approfondire `qui <https://docs.nethesis.it/Contatti_della_rubrica_NethCTI_sul_telefono>`_.

Report centralino
-----------------

È possibile visualizzare lo storico delle chiamate eseguite e ricevute
da tutti gli utenti. È inoltre possibile vedere lo storico degli SMS
inviati, le note e i POST-IT creati.


Log chiamate
------------

È possibile visualizzare lo storico delle chiamate eseguite e ricevute
relativamente al proprio utente. È inoltre possibile vedere lo storico
degli SMS inviati, le note create e i POST-IT creati. Più precisamente,
se le note sono state create con visibilità *"privata"*, allora saranno
visibili solo le proprie, altrimenti anche quelle degli altri utenti.


Customer card
-------------

Mostra la scheda cliente relativa a un numero telefonico.
È possibile visualizzarla in due modi:

#. cliccando un risultato della ricerca in rubrica
#. utilizzando il programma :doc:`nethifier`

Nel primo caso i dati della scheda cliente vengono recuperati in base al
numero telefonico di lavoro del contatto. È comunque possibile cambiare
il tipo di numero su cui effettuare la ricerca attraverso le opzioni dell'utente.

Nel secondo caso le informazioni vengono recuperati usando il numero chiamante.

Configurazione
------------------

È suddiviso in due macro sezioni:

* **sinistra**: configura lo stato dei propri interni telefonici
* **destra**: configura le opzioni relative all'utente

Stato interni telefonici
^^^^^^^^^^^^^^^^^^^^^^^^

Configura tre modalità di trasferimento di chiamata:

- *incondizionato*: qualsiasi chiamata in ingresso viene redirezionata
- *non disponibile*: la chiamata in ingresso viene redirezionata dopo un certo timeout
- *occupato*: la chiamata in ingresso viene redirezionata quando l'interno telefonico è già impegnato in un'altra conversazione

.. note::
 se abilitato, ciascun trasferimento viene attivato su tutti gli interni telefonici associati all'utente.

Opzioni dell'utente
^^^^^^^^^^^^^^^^^^^

**Cerca scheda cliente su**
    ricerca la scheda cliente sul tipo di numero telefonico selezionato.

**Url parametrizzato**
    configura l'url parametrizzato da richiedere durante una conversazione tramite il click dell'apposito pulsante presente nel box di gestione chiamata in alto. Le keywords da inserire nell'url sono:

    - *$CALLER_NAME*: nome del chiamante
    - *$CALLER_NUMBER*: numero chiamante
    - *$CALLED*: numero chiamato

    In tal modo è possibile richiamare agevolmente un gestionale o altra applicazione esterna.

**Interno predefinito**
    È l'interno telefonico associato all'utente che verrà automaticamente scelto per effettuare una telefonata. Viene indicata anche la marca, modello e versione del firmware.

**Click2Call**
    Se il telefono è supportato è possibile scegliere la modalità automatica, che farà partire automaticamente la telefonata senza la necessità di alzare la cornetta. Molto utile ad esempio con l'utilizzo di un dispositivo dotato di cuffie.

    Il pulsante :dfn:`Test echo` testa le credenziali, che devono essere quelle configurate nel telefono attraverso l'interfaccia web del dispositivo stesso. Esegue una telefonata al dispositivo stesso.

.. note:: Per utilizzare la modalità automatica è necessario configurare il telefono attraverso la sua interfaccia web. Completare il campo *"TrustedActionURIServerList"* (Webpage -> Phone Features -> ip_security -> TrustedActionURIServerList)
   con l'elenco degli indirizzi IP da cui il telefono può ricevere comandi tramite Action URI.

   Ad esempio è possibile inserire l'IP della propria rete LAN con l'ultimo campo uguale ad '*' (es. 192.168.5.*) per abilitare il telefono alla ricezione di comandi da qualsiasi pc della propria rete. Altrimenti elencare gli IP separati da virgole.

   Il nome del campo potrebbe essere diverso in base alla marca del telefono.

   **La prima volta che si utilizza il click2call automatico è possibile che il telefono mostri un messaggio per accettare la richiesta. In tal caso confermare.**

   I modelli supportati sono Yealink e Snom.

**Notifiche**

    Riguarda le notifiche di tipo :dfn:`offline`, cioè da ricevere quando non si è loggati a |product|. L'utente può ricevere notifiche per nuovi POST-IT e nuovi messaggi vocali. Sono disponibili due tipi di notifiche, *e-mail* ed *sms*. Tale funzionalità richiede che all'utente sia stato associato un endpoint di tipo cellulare e uno di tipo e-mail tramite la `configurazione utenti <configuration.html#utenti>`_.


Notifiche Online
----------------

Vengono visualizzate cliccando l'apposito pulsante presente nella barra
superiore e notificano in tempo reale gli eventi che riguardano i
servizi in background:

#. *nuovi POST-IT*
#. *nuovi messaggi di chat*
#. *nuovi messaggi vocali*


Gli elementi di notifica sono interattivi e consentono con un singolo
click di accedere alle funzionalità relative.

Voicemail
---------

È possibile ascoltare, effettuare il download del file audio ed eliminare tutti i messaggi delle caselle
vocali associate all'utente. È necessario associare almeno una :ref:`voicemail <user_configuration_ref_label>`
all'utente e deve essere attivata la funzionalità di casella vocale nel relativo interno
telefonico tramite l'interfaccia di configurazione di |parent_product|.

Pannello operatore
------------------

Utenti
^^^^^^

Il pannello operatore consente la visualizzazione completa e
l'interazione in tempo reale con tutti gli *interni e fasci*.
È possibile effettuare le seguenti operazioni su una telefonata:

-  *avviarla*
-  *terminarla*
-  *visualizzarne la durata*
-  *registrarla*
-  *ascoltare/intervenire nella conversazione*

È inoltre possibile interagire velocemente con gli interni:

-  *iniziare una conversazione di chat*
-  *creare un POST-IT*
-  *inviare un messaggio SMS*

Fasci
^^^^^

Consente la visualizzazione di tutti i fasci telefonici con il relativo stato assieme alle chiamate in transito. Ciascun fascio è suddiviso in base al numero di canali supportati.

Parcheggi
^^^^^^^^^

Visualizza lo stato dei parcheggi.


Barra Telefonica Call Center
----------------------------

Consente la visualizzazione delle code a cui appartiene il proprio interno telefonico. L'utente ha sotto controllo informazioni di stato in tempo reale sugli agenti delle code e sulle code stesse, visualizzando ad esempio le chiamate in attesa e quelle servite. Inoltre può eseguire delle azioni sul proprio interno telefonico:

* login/logout su una o più code
* entrare/uscire dallo stato di pausa

.. note:: È possibile attivare il login/logout automatico dalle code in corrispondenza del login/logout da |product| tramite la configurazione.


Fuori Orario
------------

Consente la gestione del servizio notte. L'utente può configurare l'ascolto di un messaggio audio per un certo intervallo temporale, ad esempio in corrispondenza delle vacanze estive.

Un insieme di tab mostra le varie selezioni passanti (è necessario avere il permesso "offhour") e le rotte in ingresso generiche (permesso "admin_offhour") le quali hanno un servizio notte associato. L'utente può abilitare o meno un messaggio audio con un eventuale redirezione su voicemail o può abilitare il comportamento configurato tramite l'usuale interfaccia web di |parent_product|.

Tramite la "Gestione annunci" è possibile caricare un file audio o registrarlo tramite telefono. Ogni messaggio è univocamente identificato tramite la sua *descrizione* e il *nome utente* di chi l'ha creato. È possibile scegliere tra due livelli di visibilità: *pubblica* e *privata*. Qualora venga selezionata la visibilità pubblica, altri utenti possono utilizzare quel messaggio per i propri servizi notte.


.. _streaming-video-label:

Video Streaming
---------------

È possibile visualizzare flussi video provenienti da diverse sorgenti
aggiunte attraverso il modulo di configurazione di |parent_product|, ad esempio
videocitofoni o telecamere IP. È inoltre possibile comandare l'apertura di una porta sex il dispositivo lo supporta.

.. note:: Per comandare l'apertura della porta associata al videocitofono è necessario aver prima risposto alla chiamata, oppure aspettare il termine della stessa.


Speed Dial
----------

È la lista dei contatti presente lateralmente nella sezione di sinistra.
Consente una rapida esecuzione delle operazioni più comuni su due liste
di contatti:

**speed dial**
    viene personalizzata dall'utente creando dei propri *contatti privati*
    nella rubrica |product|. L'utente può inviare una telefonata col contatto
    semplicemente con un click.

**tutti gli utenti**
    visualizza tutti gli utenti. Soffermando il mouse sul singolo utente è possibile
    visualizzare un insieme di operazioni in base al suo stato.


Ultime chiamate
---------------

È l'elenco delle ultime dieci chiamate effettuate e ricevute. Soffermando il mouse sulla singola chiamata è possibile vedere informazioni più dettagliate.

Chat
----

Per poter iniziare una conversazione di chat con un utente è sufficiente soffermare il mouse sul contatto della lista di tutti gli utenti e cliccare sull'icona relativa.

.. note:: Per poter utilizzare la chat è necessario essere collegati a |product| usando il nome di dominio del server.


.. _config_webrtc_phone-label:

Telefono integrato WebRTC
=========================

Una volta :ref:`configurato <webrtc_phone-label>` è necessario inserire (solamente la prima volta) la password dell'interno telefonico tramite la sezione configurazione utente e cliccare il pulsante per attivarlo.


Multi Sede
==========

Tramite il *multi sede* è possibile visualizzare le sedi remote :ref:`precedentemente configurate <multi_site_config-label>` ed eseguire le seguenti operazioni tramite un telefono fisico:

* chiamare un interno remoto
* chiamare un cellulare
* inviare un sms
* inviare un post-it

Le sedi remote vengono visualizzate nel pannello operatore e nella lista utenti.
Nel caso in cui la connessione con le sedi remote dovesse in qualche modo fallire, è sufficiente attendere che venga ristabilita automaticamente (il tempo impiegato è circa un minuto).

.. note:: Al momento il telefono SIP WebRTC non è supportato per chiamare utenti su sedi remote tramite il pannello operatore. È comunque possibile farlo inserendo il numero telefonico nel box di ricerca in alto.
