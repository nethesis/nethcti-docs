============
Introduzione
============

|product| è il nuovo modulo di |parent_product| che oltre alle funzioni standard di gestione chiamata da PC, introduce un pannello posto operatore, un accesso alla rubrica centralizzata, notifiche delle chiamate entranti, consultazione della scheda cliente del chiamante e altro ancora.

Tali schede possono contenere informazioni recuperate da qualsiasi gestionale e visualizzate in base al profilo dell'utente (commerciale, tecnico, amministrativo, ecc...).

A partire dalla versione 2.0 |product| è composto da cinque parti:

* :dfn:`un modulo per la configurazione su` |parent_product|
* :dfn:`il server`
* :dfn:`il client`
* :dfn:`il Posto Operatore (PO)`
* :dfn:`il Gestore delle Code Avanzato`

Il modulo di configurazione è usato per configurare il server |product| che a sua volta sarà utilizzato sia dal client, sia dal Pannello Operatore, sia dal |product_queueman|.

I client sono testati su Google Chrome e Mozilla Firefox. Tutti gli altri browser non sono attualmente supportati.
La nuova versione 2.0 abbandona l'integrazione con il CRM.

Si consiglia di utilizzare i client con monitor che abbiano una risoluzione maggiore di 1024x768 pixel.


Requisiti Minimi
================

Per poter installare la versione |version| di |product| è necessario avere installato:

* |product_nethserver|: |parent_product| `11.4 o superiore <http://nethvoice.docs.nethesis.it/it/latest>`_
* |product_nethservice| 8.2: |parent_product| 11.3 o superiore

.. note::
   Gli aggiornamenti di |product| sono manuali per |product_nethservice| 8.2
