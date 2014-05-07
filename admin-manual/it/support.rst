========
Supporto
========

Richiesta di supporto tecnico
=============================

Prima di richiedere supporto, assicurarsi che tutti i client si colleghino al server utilizzando il Fully Qualified Domain Name (FQDN) e quindi che risolvano correttamente il nome del server.

Tutte le richieste possono essere inoltrate via ticket a supporto@nethesis.it. Ciascuna richiesta dovrà:

* riportare la dicitura :dfn:`"NethCTI2"` nel campo oggetto
* contenere i dati per l'accesso SSH alla macchina (indispensabile per fornire assitenza)
* indicare le seguenti informazioni sul client utilizzato:
 * `versione del browser`
 * `versione del sistema operativo`
 * `se possibile, le credenziali di accesso dell'utente`
 * `versione dei pacchetti installati:`

 ::

  rpm -q nethcti nethcti-server nethvoice-module-nethcti nethcti-nethvoice-module neth-oppanel neth-queueman


Supporto Third-Party application
================================

È possibile integrare :index:`applicazioni di terze parti` con |product| sfruttando le sue API. Il meccanismo di base delle chiamate REST API prevede una prima fase d'autenticazione tramite le credenziali dell'utente.

Per mantenere compatibilità con le applicazioni già sviluppate che usano le API delle versione 1.x, |product| offre anche la possibilità di fare telefonate invocando una particolare API senza autenticazione. **Questa funzionalità è disabilitata di default per motivi di sicurezza.**

**Per attivarla eseguire:**

::

 config setprop nethcti-server UnAutheCall enabled
 signal-event nethcti-server-update


Una volta attivata è possibile fare una telefonata eseguendo la richiesta HTTP GET:

::

 https://<SERVER>/webrest/astproxy/unauthe_call/:endpoint/:number


dove :dfn:`:endpoint` deve essere sostituito con l'interno telefonico che si vuole utilizzare e *:number* deve essere sostituito con il numero da chiamare.

Esempio per chiamare il numero *0721405516* tramite l'interno *214* tramite il server *nethvoice.server.it*:

::

 https://nethvoice.server.it/webrest/astproxy/unauthe_call/214/0721405516

Può essere utilizzato anche il protocollo HTTP.


.. warning::

   se abilitata, chiunque può eseguire telefonate da qualsiasi interno verso qualsiasi destinazione tramite una richiesta HTTP GET.


*Per disabilitarla eseguire:*

::

  config setprop nethcti-server UnAutheCall disabled
  signal-event nethcti-server-update
