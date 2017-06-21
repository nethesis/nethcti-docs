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

Configurare un server LDAP esterno
==================================

Lista utenti da server LDAP esterno
-----------------------------------

Per ricavare la lista utenti da un server LDAP esterno è necessario collegarsi alla pagina di configurazione
di |parent_product| sezione *Utenti* e cliccare nella parte *Avanzate*.

Configurare i parametri di connessione al server ldap esterno:

* *Username*: utente abilitato per il collegamento LDAP
* *Password*: password dell'utente utilizzato per il collegamento
* *Server*: indirizzo del server LDAP esterno, utilizzare la sintassi ldap://IP o ldaps://IP
* *Port*: porta di connessione, solitamente ldap su porta 389, ldaps su porta 636
* *Base DN*: base dn ldap, solitamente dc=dominio,dc=estensione 
* *OU*: Organizational Unit ldap 
* *Type*: tipo di connessione, inserire ldap

Esempio per ricavare la lista utenti da un altro |product_nethserver|, sostituire le voci variabili (**ip_server**, **dominio_server**, **estensione**):

* *Username*: libuser
* *Password*: ricavare la password sul |product_nethserver| con la base utenti con il comando: ::

        perl -e 'use NethServer::Directory; my $password = NethServer::Password::store('libuser'); printf ($password);'

* *Server*: ldaps://**ip_server**
* *Port*: 636
* *Base DN*: dc= **dominio_server**,dc= **estensione**
* *OU*: People
* *Type*: ldap


Configurare l'autenticazione su un server LDAP esterno
------------------------------------------------------

Configurare il tipo d'autenticazione come "ldap": ::

    config setprop nethcti-server AuthType "ldap"

Configurare i parametri di connessione al server ldap esterno tramite i seguenti comandi: ::

    config setprop nethcti-server LdapBaseDN <BASE_DN>
    config setprop nethcti-server LdapOu <OU>
    config setprop nethcti-server LdapPort <LDAP_PORT>
    config setprop nethcti-server LdapServer <LDAP_SERVER>
    config setprop nethcti-server LdapsSelfSigned (true|false)

*LdapsSelfSigned* è la prop che consente di rifiutare i certificati self-signed. Il valore di default è false, quindi i certificati self-signed vengono accettati di default.

Esempio: ::

    config setprop nethcti-server AuthType "ldap"
    config setprop nethcti-server LdapBaseDN "dc=mycompany,dc=local"
    config setprop nethcti-server LdapOu "Users"
    config setprop nethcti-server LdapPort "389"
    config setprop nethcti-server LdapServer "192.168.5.111"
    config setprop nethcti-server LdapsSelfSigned false

.. note:: Per configurare ldap sicuro con SSL usare la porta 636.

Come ultima operazione eseguire: ::

    signal-event nethcti-server-update

Configurazione su Active Directory
==================================

Lista utenti da Active Directory
--------------------------------

Per ricavare la lista utenti da Active Directory è necessario collegarsi alla pagina di configurazione
di |parent_product| sezione *Utenti* e cliccare nella parte *Avanzate*.

Configurare i parametri di connessione al server ldap esterno:

* *Username*: utente abilitato al collegamento Active Directory, utilizzare la sintassi utente@dominio.estensione
* *Password*: password dell'utente utilizzato per il collegamento
* *Server*: indirizzo del server Active Directory, utilizzare la sintassi ldap://IP
* *Port*: porta di connessione, solitamente su porta 389
* *Base DN*: base dn di Active Directory, solitamente dc=dominio,dc=estensione
* *OU*: Organizational Unit Active Directory che contiene gli utenti
* *Type*: tipo di connessione, inserire AD

Configurare l'autenticazione su Active Directory
------------------------------------------------

Configurare il tipo d'autenticazione come "activeDirectory": ::

    config setprop nethcti-server AuthType "activeDirectory"

Configurare i parametri di connessione al server Active Directory tramite i seguenti comandi: ::

    config setprop nethcti-server LdapBaseDN <BASE_DN>
    config setprop nethcti-server LdapOu <OU>
    config setprop nethcti-server LdapPort <LDAP_PORT>
    config setprop nethcti-server LdapServer <LDAP_SERVER>

Esempio: ::

    config setprop nethcti-server AuthType "activeDirectory"
    config setprop nethcti-server LdapBaseDN "dc=mycompany,dc=local"
    config setprop nethcti-server LdapOu "Users"
    config setprop nethcti-server LdapPort "389"
    config setprop nethcti-server LdapServer "192.168.5.111"

Come ultima operazione eseguire: ::

    signal-event nethcti-server-update

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
