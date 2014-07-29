========
Supporto
========

Prima analisi
=============

Prima di richiedere supporto può rivelarsi utile analizzare il file di log: spesso aiuta ad individuare
immediatamente il problema. Il file di log di |product| é: ::

 /var/log/asterisk/nethcti.log

Richiesta di supporto tecnico
=============================

Prima di richiedere supporto, assicurarsi che tutti i client si colleghino al server utilizzando il Fully Qualified Domain Name (FQDN) e quindi che risolvano correttamente il nome del server.

Tutte le richieste possono essere inoltrate via ticket a supporto@nethesis.it. Ciascuna richiesta dovrà:

* riportare la dicitura :dfn:`"NethCTI2"` nel campo oggetto
* contenere i dati per l'accesso SSH alla macchina (indispensabile per fornire assistenza)
* indicare le seguenti informazioni sul client utilizzato:
 * `versione del browser`
 * `versione del sistema operativo`
 * `se possibile, le credenziali di accesso dell'utente`
 * `versione dei pacchetti installati:`

 ::

  rpm -q nethcti nethcti-server nethcti-nethvoice-module neth-oppanel neth-queueman


Troubleshooting
==============

Comandi utili
-------------

========================================= =======================================================
Comando                                   Descrizione
========================================= =======================================================
``tail -f /var/log/asterisk/nethcti.log`` Mettersi in tail sul log
``service nethcti-server restart``        Riavvio del server |product| su |product_nethservice|
``restart nethcti-server``                Riavvio del server |product| su |product_nethserver|
``signal-event nethcti-server-update``    Espansione dei templates e riavvio del server |product|
========================================= =======================================================

In qualsiasi caso
-----------------

#. I pacchetti installati sono aggiornati all'ultima versione rilasciata ?
#. Il log riporta particolari errori ? ``/var/log/asterisk/nethcti.log``

Il login fallisce
-----------------

#. L'utente esiste nel sistema ?
#. L'utente è stato configurato tramite il modulo di |parent_product| ? Cioè è stato associato almeno un interno?
#. Le credenziali sono corrette ?
#. Il server è raggiungibile ?
#. Il server riceve la richiesta di login ?

La chat non funziona
--------------------

#. Il client risolve il nome di dominio ?
#. L'url usato per accedere a |product| utilizza il nome di dominio ?

L'accesso remoto non funziona
-----------------------------

#. Le porte 443 e 8181 sono aperte verso l'esterno ?

Il click2call automatico non funziona
-------------------------------------

#. Il telefono è uno Yealink o Snom ?
#. L'utente ha selezionato la modalità "automatica" nelle preferenze all'interno di |product| ?
#. L'utente ha inserito le credenziali del telefono nelle preferenze all'interno di |product| ?
#. Cosa succede utilizzando il tasto "Test Echo" nelle preferenze all'interno di |product| ?
#. Le telefonate funzionano usando la modalità manuale ?
#. Lo stato dell'interno telefonico con cui è configurato il telefono, risulta online in asterisk ?
#. L'ip del proprio pc è stato abilitato nelle impostazioni di sicurezza del telefono ?
#. Durante il primo utilizzo, si è accettata la richiesta mostrata sul display del telefono ?

L'invio SMS fallisce
--------------------

#. Controllare la configurazione tramite l'interfaccia grafica di |parent_product|.
#. Se si utilizza il PORTech:
    * è raggiungibile ? (Tentare una connessione tramite telnet)
    * è possibile forzare l'invio immediato dei messaggi accodati tramite lo script ``/usr/lib/node/nethcti-server/scripts/sendsms.php``


Altro
-----

#. Mettersi in tail sul log e fare un refresh della pagina di |product|: che errori riporta ?
#. Mettersi in tail sul log e riavviare il servizio: che errori riporta ?
#. Il comando specifico per il riavvio del server |product| riesce effettivamente a riavviarlo ? (Controllare il PID del processo).
