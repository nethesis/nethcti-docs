=========================
Personalizzazione servizi
=========================

È possibile personalizzare la configurazione di alcuni servizi solo manualmente attraverso la linea di comando.

Attivazione del debug
=====================

Di default il file di log riporta solamente messaggi di warning ed errori. È possibile innalzare il livello di debug per avere maggiori informazioni: ::

 config setprop nethcti-server LogLevel info
 signal-event nethcti-server-update

Per ripristinare il livello di debug: ::

 config setprop nethcti-server LogLevel warn
 signal-event nethcti-server-update

.. warning:: Innalzando il livello la dimensione del file di log aumenta rapidamente.

Configurazione Chat
===================

È possibile personalizzare il protocollo utilizzato dal client per connettersi al server ejabberd. ::

    config setprop nethcti-server Protocol "https"
    signal-event nethcti-server-update

I valori possibili sono *http* o *https*.


Configurare un prefisso telefonico
==================================

Per configurare un prefisso per tutte le chiamate: ::

 config setprop nethcti-server Prefix 0039
 signal-event nethcti-server-update

Per rimuoverlo: ::

 config setprop nethcti-server Prefix ""
 signal-event nethcti-server-update

Personalizzare il mittente degli SMS
====================================

Se si utilizza *smshosting* come servizio web per l'invio degli SMS, è possibile personalizzare
il nome del mittente dei messaggi. È sufficiente aggiungere il seguente parametro all'url da inserire
nel pannello di configurazione di |parent_product|: ::

  mittente=nome_da_usare


Eseguire uno script per ogni chiamata eseguita
==============================================

È possibile configurare |product| per eseguire uno script in corrispondenza di ogni chiamata terminata. Lo script riceverà come parametri i dati relativi alla telefonata. Per abilitarlo: ::

 config setprop nethcti-server CdrScript <SCRIPT_PATH>
 config setprop nethcti-server CdrScriptTimeout <TIMEOUT_MILLISECONDS>
 signal-event nethcti-server-update

Il valore di default per il timeout è pari a 5 secondi, ma può essere configurato a piacere.
