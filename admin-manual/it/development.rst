========
Sviluppo
========

Autenticazione
==============

Lo scopo della fase d'autenticazione è creare un *token* che sarà usato per invocare le REST API.

Eseguire il login
-----------------

1. Il client invia una richiesta HTTP (POST) alla seguente rest api:

::

 https://<SERVER>/webrest/authentication/login

specificando lo _username_ e _password_ in formato JSON:

::

 { "username": "pippo", "password": "pluto" }

2. Il client riceve una risposta standard HTTP 401. Se l'autenticazione ha avuto successo la risposta contiene un _nonce_ (un numero) nello header HTTP, altrimenti l'autenticazione è fallita. Un esempio di header è (il nonce è *06d15944d8ece69bdc97742b37c507970e2f6651*):

::

 www-authenticate: Digest 06d15944d8ece69bdc97742b37c507970e2f6651

3. Il client calcola il token:

::

 tohash = username + ':' + password + ':' + nonce
 token  = HMAC-SHA1(tohash, password)

4. Il client memorizza il token per usi futuri.

**Se il token d'autenticazione non viene mai usato, scade dopo un certo periodo di tempo (il default è mezz'ora). Una nuova fase d'autenticazione è necessaria.**


Eseguire il logout
------------------

1. Il client invia una richiesta HTTP (POST) alla seguente rest api:

::

    https://<SERVER>/webrest/authentication/logout

2. Il token viene rimosso dal server.

REST API
========

Le REST API sono dei Web Services che consentono l'interazione con il server |product|. È uno strumento molto utile per l'integrazione e lo sviluppo ed è la miglior soluzione da utilizzare con applicazioni mobile.

.. note::

 Questo documento assume che il lettore possegga già una certa familiarità con le più comuni tecniche di programmazione e Web Services.

Caratteristiche comuni
----------------------

Di seguito vengono elencate le caratteristiche comuni a tutte le REST API:

* una API viene invocata tramite l'invio di una richiesta HTTP al server |product| che risponde fornendo i dati richiesti o tramite un codice di stato o entrambi.
* Tutte le risorse sono raggiungibili tramite l'url:

::

  http[s]://<SERVER>/webrest/

* Per richiedere una API è necessario aggiungere un *path* al baseurl che specifica la risorsa da richiedere. Per esempio:

::

  http[s]://<SERVER>/webrest/phonebook/search

* Ogni richiesta deve contenere i parametri d'autenticazione per il controllo d'accesso.
* Ogni richiesta viene *autenticata* e *autorizzata* del server |product|.


Autenticazione
--------------

#. Il client deve eseguire il login e deve creare un token d'autenticazione come descritto `qui <https://dev.nethesis.it/projects/asterisk-cti/wiki/Authentication>`_.
#. Per ogni richiesta rest api il client deve configurare lo HTTP header:

::

    Authorization: username:token

La validità del token d'autenticazione viene aggiornato ad ogni richiesta, altrimenti scade come descritto `qui <https://dev.nethesis.it/projects/asterisk-cti/wiki/Authentication#How-to-login>`_.


Autorizzazione
--------------

Ogni richiesta REST API viene autorizzata dal server che controlla i permessi utente configurati dall'amministratore attraverso l'interfaccia di |parent_product|.



WebSocket
=========

La connessione WebSocket viene utilizzata dal server per comunicare in tempo reale con tutti i client connessi (ad esempio per notificare gli eventi del server Asterisk).
Per stabilire una connessione WebSocket col server |product| è necessaria una prima fase d'autenticazione.

Eseguire il login
-----------------

#. Il client esegue il login e crea un nuovo token d'autenticazione come descritto `qui <https://dev.nethesis.it/projects/asterisk-cti/wiki/Authentication>`_.
#. Il client stabilisce una connessione websocket con il server (la porta di default sicura è la 8181).
#. Il client invia il messaggio *login* al server attraverso la connessione websocket specificando *username* e *token* in formato JSON:

::

 socket.emit('login', { accessKeyId: username, token: token.toString() });

#. Se il login ha avuto successo il client riceve il messaggio *authe_ok*, altrimenti il messaggio *401* e il client viene disconnesso.

**Una volta completato il login con successo, il token ha validità infinita fino al riavvio del server.**


Integrazione di applicazioni legacy
===================================

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
