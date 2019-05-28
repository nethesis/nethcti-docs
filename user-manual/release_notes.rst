================
Note di rilascio
================

Cambiamenti principali - v3.13.0 - (28 MAG 2019)
================================================

**Nuove funzionalità e miglioramenti**

- Inserita una nuova dashboard all'interno del servizio QManager (Supervisore delle code). Il servizio consente una visualizzazione di differenti tipi di allarmi riguardanti le code

  - `documentazione <https://nethcti.docs.nethesis.it/it/v3/qmanager.html#dashboard>`_
  - `issue 5631 <https://github.com/nethesis/dev/issues/5631>`_
  - `issue 5621 <https://github.com/nethesis/dev/issues/5621>`_

- Aggiunta la possibilità di eseguire uno script lato server al termine di una chiamata

  - `documentazione <https://nethvoice.docs.nethesis.it/it/v14/howto.html#product-cti-eseguire-uno-script-al-termine-di-una-chiamata>`_
  - `issue 5613 <https://github.com/nethesis/dev/issues/5613>`_

- `Migliori performance operative del pannello operatore in presenza di un elevato numero di gruppi utente <https://github.com/nethesis/dev/issues/5624>`_
- `Aggiornamento della libreria janus (alle ultime modifiche upstream) utilizzata per il telefono WebRTC <https://github.com/nethesis/dev/issues/5633>`_

**Bug fixes**

- `Risolto il problema dell'errata direzione delle chiamate in ringing mostrate nel pannello operatore <https://github.com/nethesis/dev/issues/5629>`_
- `Risolto il problema del reset dello stato di prensence in un particolare scenario operativo <https://github.com/nethesis/dev/issues/5628>`_
- `Risolto il problema della non risposta a una chiamata usando il telefono WebRTC in particolari scenari operativi <https://github.com/nethesis/dev/issues/5633>`_

**Pacchetti coinvolti**

- ``nethserver-nethvoice14-14.2.8-1.ns7.noarch.rpm``
- ``janus-gateway-0.7.0.7-1.ns7.x86_64.rpm``
- ``nethserver-janus-1.0.12-1.ns7.noarch.rpm``
- ``nethcti3-3.13.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.13.0-1.ns7.x86_64.rpm``

Cambiamenti principali - v3.12.0 - (17 APR 2019)
================================================

**Nuove funzionalità e miglioramenti**

- `Nuovo servizio "Monitor" all'interno del QManager: consente di tenere sotto controllo in tempo reale le chiamate in attesa nelle code abilitate <https://github.com/nethesis/dev/issues/5602>`_

**Bug fixes**

- `Risolto il problema della registrazione delle chiamate <https://github.com/nethesis/dev/issues/5615>`_
- `Risolto il problema che in alcuni casi non mostrato il box di gestione chiamata durante lo spy di una conversazione <https://github.com/nethesis/dev/issues/5612>`_
- `A volte l'invocazione della rest api astproxy/qmanager_astats generava un errore nel file di log <https://github.com/nethesis/dev/issues/5611>`_
- `La rest api astproxy/extension/:id restituiva solamente il proprio interno telefonico <https://github.com/nethesis/dev/issues/5609>`_
- `La rest api history/interval non funzionava correttamente usando il valore "user" come parametro "type" <https://github.com/nethesis/dev/issues/5608>`_

**Pacchetti coinvolti**

- ``nethcti3-3.12.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.12.0-1.ns7.x86_64.rpm``

Cambiamenti principali - v3.11.0 - (1 APR 2019)
================================================

**Nuove funzionalità e miglioramenti**

- `Per gli sviluppatori: i dati contenuti all'interno dell'oggetto JSON "Conversations" restituito attraverso la REST API "astproxy/extensions" o attraverso gli eventi WebSocket, ora contiene anche l'informazione "linkedid" che sarà presente nel database dello storico delle chiamate "asteriskcdrdb.cdr" al termine della chiamata stessa <https://github.com/nethesis/dev/issues/5605>`_
- `Aggiornamento della libreria Janus usata per il softphone WebRTC alla versione 0.6.3 <https://github.com/nethesis/dev/issues/5601>`_

**Bug fixes**

- `Risolto il problema che causava il riavvio di NethCTI in corrispondenza di modifiche apportate alla configurazione tramite wizard <https://github.com/nethesis/dev/issues/5600>`_

**Pacchetti coinvolti**

- ``nethcti3-3.11.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.11.0-1.ns7.x86_64.rpm``
- ``janus-gateway-0.6.3-1.ns7.x86_64.rpm``
- ``nethserver-janus-1.0.10-1.ns7.noarch.rpm``

Cambiamenti principali - v3.10.1 - (22 MAR 2019)
================================================

**Bug fixes**

- `Risolto un problema di compatibilità con la prossima versione di Asterisk 13.23+ <https://github.com/nethesis/dev/issues/5597>`_
- `Eseguendo una telefonata verso una destinazione in stato di occupato, non si sentiva il tono di occupato <https://github.com/nethesis/dev/issues/5593>`_

**Pacchetti coinvolti**

- ``nethcti3-3.10.1-1.ns7.noarch.rpm``
- ``nethcti-server3-3.10.1-1.ns7.x86_64.rpm``

Cambiamenti principali - v3.10.0 - (15 MAR 2019)
================================================

**Nuove funzionalità e miglioramenti**

- `Aggiornamento della libreria Janus alla versione 0.6.2 <https://github.com/nethesis/dev/issues/5590>`_
- `Aggiornamento di NodeJS alla versione 10 <https://github.com/nethesis/dev/issues/5588>`_
- `Possibilità di personalizzare il messaggio di warning in corrispondenza del login da parte di un utente non configurato <https://github.com/nethesis/dev/issues/5585>`_

**Bug fixes**

- `Aggiornamento di sicurezza di alcune librerie <https://github.com/nethesis/dev/issues/5587>`_
- `Risolto un problema sulla rest api "historycall/interval" <https://github.com/nethesis/dev/issues/5584>`_
- `Risolto il problema del login/logout automatico dalle code quando si è utilizzato il proprio interno telefonico come username per il login <https://github.com/nethesis/dev/issues/5581>`_

**Pacchetti coinvolti**

- ``nethcti3-3.10.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.10.0-1.ns7.x86_64.rpm``
- ``nethserver-janus-1.0.9-1.ns7.noarch.rpm``
- ``janus-gateway-0.6.2-1.el7.x86_64.rpm``

Cambiamenti principali - v3.9.0 - (8 FEB 2019)
==============================================

**Nuove funzionalità e miglioramenti**

- `Nuova app "Post Operatore Avanzato" integrato all'interno di NethCTI <https://github.com/nethesis/dev/issues/5549>`_

**Bug fixes**

- `Entrando nelle code da NethCTI la "penalità" degli agenti delle code non veniva rispettata <https://github.com/nethesis/dev/issues/5575>`_

**Pacchetti coinvolti**

- ``nethcti3-3.9.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.8.0-1.ns7.x86_64.rpm``
- ``nethserver-nethvoice14-14.2.2-1.ns7.noarch.rpm``
- ``nethvoice-wizard-restapi-14.2.1-1.ns7.noarch.rpm``
- ``nethvoice-wizard-ui-14.2.1-1.ns7.noarch.rpm``

Cambiamenti principali - v3.8.0 - (24 GEN 2019)
===============================================

**Nuove funzionalità e miglioramenti**

- `La dimensione dei dati trasferiti dal server è stata ridotta del 73% <https://github.com/nethesis/dev/issues/5568>`_

**Bug fixes**

- `Durante la creazione di un contatto speeddial, alcune label per scegliere il "Numero preferito" erano errate <https://github.com/nethesis/dev/issues/5570>`_
- `Il pannello operatore, in presenza di molti gruppi, ne nascondeva alcuni. Ora è possibile vederli tutti grazie alla presenza di una scrollbar orizzontale <https://github.com/nethesis/dev/issues/5570>`_
- Il pulsante "Pausa" presente nel box di gestione chiamata, non funzionava correttamente quando la chiamata non era tra due interni. Questo bug è stato introdotto nella precedente release 3.7.0 per cercare di mitigare il problema associato (`5562 <https://github.com/nethesis/dev/issues/5562>`_)
  - `issue 5569 <https://github.com/nethesis/dev/issues/5569>`_

**Pacchetti coinvolti**

- ``nethcti3-3.8.0-1.ns7.noarch.rpm``

Cambiamenti principali - v3.7.0 - (21 GEN 2019)
===============================================

**Nuove funzionalità e miglioramenti**

- `Muovendo il mouse sopra un risultato di una ricerca in rubrica, più specificatamente sull'icona che rappresenta la sorgente dati, appare un tooltip. Questo è stato reso maggiormente esplicativo, mostrando la sorgente dati specifica (se presente) <https://github.com/nethesis/dev/issues/5566>`_
- `La rimozione di un messaggio audio del servizio "Fuori Orario" viene ora loggato nel server come messaggio di warning <https://github.com/nethesis/dev/issues/5565>`_
- `Ciascun box utente all'interno del "Pannello operatore", mostra ora anche il numero di cellulare da poter chiamare (se è stato preventivamente associato tramite il wizard di configurazione) <https://github.com/nethesis/dev/issues/5564>`_
- `Nella lista delle ultime chiamate, è stata aggiunta la visualizzazione del campo "azienda" per le chiamate in uscita <https://github.com/nethesis/dev/issues/5558>`_

**Bug fixes**

- `Il pulsante "Pausa" all'interno del box di gestione chiamata non veniva aggiornato quando si utilizzava il telefono per entrare nello stato di attesa <https://github.com/nethesis/dev/issues/5562>`_
- `Il trasferimeno di chiamata eseguito inserendo manualmente un numero telefonico non funzionava <https://github.com/nethesis/dev/issues/5559>`_

**Pacchetti coinvolti**

- ``nethcti3-3.7.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.7.0-1.ns7.x86_64.rpm``

Cambiamenti principali - v3.6.0 - (11 GEN 2019)
===============================================

**Nuove funzionalità e miglioramenti**

- `QManager Supervisore delle code: è stata rilasciata la versione finale <https://github.com/nethesis/dev/issues/5547>`_
- `È stata aggiunta una scroolbar nella lista delle chiamate in attesa e connesse all'interno del Supervisore delle code per facilitarne la visualizzazione <https://github.com/nethesis/dev/issues/5539>`_
- Possibilità di aggiungere nuovi campi durante la creazione di nuovi contatti in rubrica

  - `issue 5536 <https://github.com/nethesis/dev/issues/5536>`_
  - `issue 5537 <https://github.com/nethesis/dev/issues/5537>`_

- `Possibilità di effettuare chiamate video anche tra telefoni fisici (codec supportati: VP8 e H.264) e Softphone WebRTC (in dipendenza del browser utilizzato: consigliato Google Chrome) <https://github.com/nethesis/dev/issues/5546>`_

**Bug fixes**

- `L'utente non vede più i servizi per i quali non possiede il relativo permesso <https://github.com/nethesis/dev/issues/5542>`_
- `Quando l'utente cambiava il dispositivo di default da Softphone WebRTC ad altro, il softphone non si deregistrava continuando ad essere operativo <https://github.com/nethesis/dev/issues/5541>`_
- `Le chiamate in uscita elencate nella lista delle ultime dieci chiamate non mostrava il nome quando presente, ma solo il numero <https://github.com/nethesis/dev/issues/5538>`_
- `Durante la modifica di un contatto in rubrica, la privacy veniva mostrata in maniera errata <https://github.com/nethesis/dev/issues/5535>`_
- `Risolto il problema della non visualizzazione del pulsante per modificare i contatti in rubrica in corrispondenza di alcuni scenari <https://github.com/nethesis/dev/issues/5533>`_
- `Risolto il problema della duplicazione delle richieste eseguite verso il server in alcuni scenari durante le ricerche in rubrica <https://github.com/nethesis/dev/issues/5533>`_
- `Dopo aver eseguito delle modifiche tramite il wizard di configurazione, sporadicamente l'utente non era più in grado di accedere a NethCTI <https://github.com/nethesis/dev/issues/5451>`_

**Pacchetti coinvolti**

- ``nethcti3-3.6.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.6.0-1.ns7.x86_64.rpm``

Cambiamenti principali - v3.5.0 - (18 DIC 2018)
===============================================

**Nuove funzionalità**

- `Sono state aggiunte 3 nuove azioni al trasferimento consultativo: <https://github.com/nethesis/dev/issues/5528>`_

  1. "*Interrompi trasferimento*": possibilità di interrompere il trasferimento
  2. "*Inizia conferenza*": possibilità di parlare con tutti e tre i partecipanti contemporaneamente
  3. "*Cambia interlocutore*": possibilità di "switchare" la conversazione da un partecipante all'altro più volte

- `Migliorata la stabilità del telefono WebRTC integrato in NethCTI grazie all'aggiornamento del componente Janus-Gateway alla versione 0.5.0 <https://github.com/nethesis/dev/issues/5519>`_
- `Migliorata la gestione degli eventi di Asterisk da parte del CTI Server, del numero di queries eseguite e del numero di eventi inviati ai clients <https://github.com/nethesis/dev/issues/5513>`_

**Bug fixes**

- `Risolto il problema della visualizzazione ritardata del box di gestione chiamata per conversazioni verso l'esterno <https://github.com/nethesis/dev/issues/5525>`_
- `Risolto il problema della scomparsa delle statistiche degli agenti del QManager <https://github.com/nethesis/dev/issues/5524>`_
- `Le conferenze audio non funzionavano correttamente quando l'utente utilizzava un telefono fisico <https://github.com/nethesis/dev/issues/5520>`_
- `Rimosse alcune REST api inutilizzate e presenti dalla versione 2.0 <https://github.com/nethesis/dev/issues/5518>`_
- `Risolti alcuni problemi di: <https://github.com/nethesis/dev/issues/5517>`_

  - ricerca nello storico chiamate
  - visualizzazione delle date durante la modifica di un rotta nel servizio Fuori Orario
  - ricerca nella rubrica: aggiunto un terzo campo per filtrare la ricerca

- `Con il livello di log a "info" le queries eseguite dal CTI Server venivano scritto sul file "messages" <https://github.com/nethesis/dev/issues/5508>`_

**Pacchetti coinvolti**

- ``nethcti3-3.5.0-1.ns7.noarch.rpm``
- ``nethcti-server3-3.5.0-1.ns7.x86_64.rpm``
- ``janus-gateway-0.5.0-1.ns7.x86_64.rpm``
- ``nethserver-janus-1.0.6-1.ns7.noarch.rpm``


Cambiamenti principali - v3.4.0 - (12 NOV 2018)
===============================================

**Nuove funzionalità**

- `Possibilità di effettuare chiamate in maniera non autenticata: <https://nethvoice.docs.nethesis.it/it/v14/howto.html#product-cti-effettuare-chiamate-in-maniera-non-autenticata>`_ un esempio di utilizzo è l'esecuzione di chiamate in software di terze parti senza sviluppare necessariamente la parte di autenticazione. Leggendo attentamente la documentazione relativa, si nota che la funzione è **disabilitata di default** e può essere selettivamente attivata per **specifici range di indirizzi IP.**

**Bug fixes**

- Risolto il problema della scomparsa del pulsante "Cambia dispositivo": durante una chiamata è possibile "passare" la conversazione su un altro dispositivo associato al proprio utente

  - https://github.com/nethesis/dev/issues/5510
  - https://github.com/nethesis/dev/issues/5511

.. image:: img/switch-device.png



Cambiamenti principali - v3.3.3 - (5 NOV 2018)
===============================================

**Bug fixes**

- `Sistemato il "freeze" del client quando si eseguiva il reload del server in presenza di centinaia di utenti configurati <https://github.com/nethesis/dev/issues/5504>`_
- `La rest api "astproxy/extension" restituiva il risultato anche in assenza dell'header HTTP Authorization <https://github.com/nethesis/dev/issues/5501>`_
- `Rimossa la doppia richiesta del client per ottenere la lista delle chiamate perse in coda: avveniva dopo un reload del server <https://github.com/nethesis/dev/issues/5500>`_
- `Dopo un reload del server e in caso di "DND on/off automatico" dell'utente scelto dal client, il log del server riportava degli errori a causa dell'esecuzione di operazioni duplicate <https://github.com/nethesis/dev/issues/5495>`_

.. _SO: http://stackoverflow.com/

Cambiamenti principali - v3.3.2 - (31 OTT 2018)
===============================================

**Bug fixes**

- `Sistemata la registrazione dei messaggi audio nel servizio "Fuori Orario" <https://github.com/nethesis/dev/issues/5492>`_
- `Rubrica: <https://github.com/nethesis/dev/issues/5485>`_

  - rimosso il pulsante "modifica" sui contatti provenienti dalla rubrica centralizzata
  - sistemata la ricerca alfabetica quando si utilizza la visualizzazione per "azienda"
  - rimosso il pulsante "speeddial" durante la modifica di un contatto non proprio
- `Il click sul popup di arrivo chiamata non portava in primo piano il tab NethCTI <https://github.com/nethesis/dev/issues/5484>`_
- `Le pagine dei servizi senza permesso erano raggiungibili anche se vuote <https://github.com/nethesis/dev/issues/5484>`_

Nuova versione |version|
========================

|product| versione |version| introduce una nuova grafica, completamente rinnovata e semplificata per l'utente finale.

Funzionalità principali:

- Configurazione semplificata attraverso il wizard di |parent_product|
- Salvataggio centralizzato sul server di tutte le preferenze utente
- Customer card più semplici da configurare e con una veste grafica completamente rivista
- Gestione device multipli associati ad un singolo utente
- Possibilità di impostare la presence in modo unificato su tutti i dispositivi
- Personalizzazione avatar
- Nuova chat (XMPP)
- Restyling grafico e funzionale del pannello operatore
- Possibilità di raggruppare i risultati della ricerca in rubrica per persona o per azienda
- Nuovo softphone WebRTC con supporto alle videochiamate (solo fra interni WebRTC)
- Visualizzazione sorgenti video anche dall'esterno della LAN
- Conferenze audio
- Configurazione servizio notte
- Code: chiamate perse, login e logout automatico
- Visualizzazione stato dei fasci
- Apertura di un url parametrizzato in corrispondenza della ricezione di una chiamata
- Nethifier
- Supervisore Code

Le seguenti funzioni non sono disponibili:

- Post-it e note chiamate
- Sedi remote
- Integrazione SMS e notifiche offline (mail e SMS)
- Inoltro della chiamata a numero o voicemail, su non disponibile/occupato
- Script personalizzati per la gestione chiamate
- Posto Operatore

.. warning:: |product| |version| necessita di |parent_product| 14
