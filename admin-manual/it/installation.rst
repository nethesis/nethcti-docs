=============
Installazione
=============

Per installare il server eseguire: ::

  yum install nethcti-server

Dall'interfaccia grafica di configurazione di |parent_product|, cliccare il pulsante "Applica cambiamenti", se presente.

Per installare il client eseguire: ::

  yum install nethcti

.. note:: Subito dopo la prima installazione è necessario procedere con la configurazione minima di utenti e profili.

Installazione chat su |product_nethserver|
=================================================

Il server chat non viene installato automaticamente con |product|, perciò per utilizzare la chat è necessario installare ``nethserver-ejabberd``: ::

 yum install nethserver-ejabberd
