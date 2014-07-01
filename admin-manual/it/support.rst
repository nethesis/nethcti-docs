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

  rpm -q nethcti nethcti-server nethvoice-module-nethcti nethcti-nethvoice-module neth-oppanel neth-queueman

