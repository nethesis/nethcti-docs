===================
|product_nethifier|
===================

|product_nethifier| Windows Integration è l'applicazione per Microsoft Windows che consente l'integrazione di |product| con il desktop Windows. In particolare consente la visualizzazione di popup di notifica nel desktop in corrispondenza della ricezione di telefonate dirette a un qualsiasi interno telefonico dell'utente.

Versioni di Windows compatibili: Windows 7 (64 bit) e Windows 8.

Per la personalizzazione dei popup seguire la :ref:`documentazione <custom-nethifier-label>`.

Requisiti
=========

- .NET Framework 4.5.
- Server |product| 2.x.
- Il pc su cui è in esecuzione |product_nethifier| deve risolvere l'indirizzo ``nomenethvoice.dominio``.

.. note:: Per ottenere il nome di dominio si può utilizzare il comando ``hostname -f``

Installazione
=============

È sufficiente effettuare il download dell'installer
ed eseguirlo. Terminata la fase d'installazione il programma verrà
avviato automaticamente.

Descrizione
===========

|product_nethifier| è sempre visibile tramite l'icona presente nella
system tray di Windows cliccando la quale appare un menu con varie opzioni.

All'arrivo di una chiamata a uno degli interni telefonici associati all'utente,
viene visualizzato un popup nel desktop che riporta informazioni sul chiamante.

Esistono due tipi di popup:

#. **generico** con informazioni sul chiamante
#. **di streaming** quando qualcuno suona al videocitofono

Il secondo tipo mostra l'immagine della persona che sta suonando il videocitofono.

È possibile interagire coi popup in diversi modi, ad esempio visualizzando la customer card del chiamante oppure comandando l'apertura della porta associata al videocitofono.

I popup sono estremamente personalizzabili, sia *nell'interfaccia grafica*, sia soprattutto nel *contenuto*. È infatti possibile aggiungere un qualsiasi comando da eseguire direttamente col click sul popup, come ad esempio l'apertura di un gestionale, l'invocazione di un url http, come anche l'esecuzione di un applicativo Java. In generale è possibile eseguire qualsiasi applicativo di Windows.

Il colore dell'icona del programma presente nella system tray indica lo stato di connessione col server cti. Il blu indica che |product_nethifier| è connesso, mentre il colore rosso indica un problema di connessione. In corrispondenza di una disconnessione di rete, che può accadere per vari motivi, |product_nethifier| tenta di riconnettersi in automatico per un certo intervallo temporale (circa 3 minuti). In ogni modo è possibile forzare la riconnessione attraverso il menù contestuale.

Configurazione
==============

È necessaria solamente la prima volta. I dati da inserire sono:

-  indirizzo del server (nome o IP)
-  credenziali dell'utente

È necessario salvare i dati cliccando il pulsante apposito in maniera tale da
non doverli più reinserire agli avvii successivi. È anche possibile scegliere
di eseguire |product_nethifier| all'avvio di windows.

Rimozione
=========

È sufficiente aprire il menu *Programmi* di Windows e cliccare la voce
"|product_nethifier| -> Uninstall".

.. _custom-nethifier-label:

Personalizzazione
=================

I :doc:`popup <nethifier>` possono essere personalizzati sia nella *grafica*, sia nel *contenuto*
attraverso i seguenti template HTML: ::

 /usr/lib/node/nethcti-server/plugins/com_static_http/static/templates/notification_popup/call.html
 /usr/lib/node/nethcti-server/plugins/com_static_http/static/templates/notification_popup/streaming.html

Il primo serve a mostrare i dati di una chiamata generica, mentre il secondo quelli di una
:ref:`sorgente video <streaming-video-label>`, quale ad esempio un videocitofono.

.. note:: Conoscenze richieste: linguaggi di programmazione HTML, CSS e Javascript.

Personalizzazione della grafica
-------------------------------

È sufficiente personalizzare il codice HTML e/o CSS dei template indicati. Supponiamo ad esempio di
voler modificare il colore del **nome e numero chiamante** in verde nel template ``call.html``: sarà sufficiente
aggiungere la regola css ``color: green`` nel selettore ``.contact-info``, che diventerà:

.. code-block:: css

    .contact-info {
        font-family: verdana;
        margin-top: 5px;
        margin-left: 15px;
        float: left;
        color: green;
    }

Personalizzazione del contenuto
-------------------------------

È possibile estendere le funzionalità presenti all'interno dei popup con nuovi comandi da eseguire.

1. Creare il template custom `win_popup.json`:

::

 mkdir -p /etc/e-smith/templates-custom/etc/nethcti/win_popup.json
 cp /etc/e-smith/templates/etc/nethcti/win_popup.json/10base /etc/e-smith/templates-custom/etc/nethcti/win_popup.json

2. Aprire il template appena creato con un editor di testi:

::

 vim /etc/e-smith/templates-custom/etc/nethcti/win_popup.json/10base

3. Aggiungere il nuovo comando all'interno dell'oggetto JSON `"commands"`, specificando
il percorso del programma eseguibile di Windows che si intenderà eseguire: ::

    ,"<NOME_NUOVO_COMANDO>": {
        "command": "<NOME_NUOVO_COMANDO>",
        "runwith": "<PATH_EXE>"
    }

Se ad esempio il nuovo comando si chiama **"gestionale"** e il programma da eseguire è
**"c:\\windows\\notepad.exe"**, la sezione da inserire sarà: ::

    ,"gestionale": {
        "command": "gestionale",
        "runwith": "c:\\\windows\\\notepad.exe"
    }


e quindi il template custom diventerà: ::

    {
        my $popupCtiProto = ${'nethcti-server'}{'PopupCtiProto'} || "https";

        $OUT = '{
        "call": {
            "width": "400",
            "height": "175"
        },
        "stream": {
            "width": "400",
            "height": "400"
        },
        "close_timeout": "10",
        "commands": {
            "url": {
                "command": "url",
                "runwith": ""
            }
            ,"gestionale": {
                "command": "gestionale",
                "runwith": "c:\\\windows\\\notepad.exe"
            }
        },
        "cti_proto": "' . $popupCtiProto .'"
    }';
    }

.. warning:: Il percorso dell'eseguibile di Windows deve utilizzare la stringa "\\\\\\" come separatore.

4. Adattare l'altezza del popup che si intende modificare, in base all'elemento grafico da aggiungere. Se ad esempio
si vuole inserire un nuovo pulsante nel template `"call.html"`, un'altezza pari a 175px può essere sufficiente:

::

    {
        "call": {
            "width": "400",
            "height": "175"
        },
        ...

5. Salvare la configurazione e uscire dall'editor di testi.

6. Eseguire il comando: ::

    signal-event nethcti-server-update

7. Personalizzare uno o entrambi i template HTML in base alle proprie necessità:
è necessario inserire un **elemento grafico** e **un'azione da eseguire** in
corrispondenza del click sullo stesso. Supponiamo ad esempio di voler inserire
un nuovo pulsante nel template *"call.html"* cliccando il quale eseguire il nuovo
comando "gestionale".

Il codice HTML del nuovo pulsante grafico da inserire in *call.html* sarà:

.. code-block:: html

    <div class="contact-action">
        <div id="open-gestionale-but" cmd="gestionale" arg="" close="1" class="button" title="">Gestionale</div>
    </div>

8. **Opzionale:**
se si desidera passare l'identificativo del chiamante come parametro al programma di Windows,
è necessario aggiungere il seguente codice javascript in coda alla funzione `window.onload`:

.. code-block:: javascript

 $('#open-gestionale-but').attr('arg', params.callerNum);

9. Eseguire |product_nethifier| in Windows e connettersi al server cti.

Da questo momento alla ricezione di una chiamata generica nel popup sarà presente
un nuovo pulsante di nome "Gestionale", cliccando il quale si aprirà il notepad di Windows.

Ogni client |product_nethifier| può inoltre personalizzare i path dei programmi da eseguire:
aprire l'interfaccia grafica |product_nethifier| attraverso la voce "Visualizza" del
menù contestuale dell'icona nella system tray di Windows, selezionare il tab "Esegui", personalizzare
i path e salvare la configurazione.

Personalizzazione del protocollo
--------------------------------

È possibili modificare il protocollo con cui aprire |product| tramite il click sul popup.
Eseguire: ::

 config setprop nethcti-server PopupCtiProto "<PROTO>"
 signal-event nethcti-server-update

dove <PROTO> può assumere i valori *http* o *https*.

Backup
------

Una volta effettuata una personalizzazione, ricordarsi di aggiungere i file alla lista dei backup
seguendo le istruzioni `qui riportate <http://docs.nethserver.org/en/latest/backup.html#inclusion>`_.


Download
========

Il download è disponibile nell'area relativa https://docs.nethesis.it/Area_Download.
