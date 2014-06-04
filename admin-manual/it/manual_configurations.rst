======================
Configurazioni manuali
======================

Alcuni parametri del server sono configurabili solo manualmente tramite la linea di comando.

Configurazione Chat
===================

È possibile personalizzare il protocollo utilizzato dal client per connettersi al server ejabberd. ::

    config setprop nethcti-server Protocol "https"
    signal-event nethcti-server-update

I valori possibili sono *http* o *https*.
