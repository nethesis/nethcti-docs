===========================================
Integrazione di applicazioni legacy
===========================================

Per mantenere compatibilità con le :index:`applicazioni legacy` che usano le API della versione 1.x, |product| offre la possibilità di fare telefonate invocando una particolare API senza autenticazione. **Questa funzionalità è disabilitata di default per motivi di sicurezza.**

**Per l'attivazione eseguire:**

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

   Se la funzionalità viene abilitata, chiunque può eseguire telefonate da qualsiasi interno verso qualsiasi destinazione tramite una richiesta HTTP GET.


**Per la disabilitazione eseguire:**

::

  config setprop nethcti-server UnAutheCall disabled
  signal-event nethcti-server-update
