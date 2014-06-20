=========================
Personalizzazione servizi
=========================

È possibile personalizzare la configurazione di alcuni servizi solo manualmente attraverso la linea di comando.

Configurazione Chat
===================

È possibile personalizzare il protocollo utilizzato dal client per connettersi al server ejabberd. ::

    config setprop nethcti-server Protocol "https"
    signal-event nethcti-server-update

I valori possibili sono *http* o *https*.

Configurare l'autenticazione su un server LDAP esterno
======================================================

Configurare il tipo d'autenticazione come "ldap": ::

    config setprop nethcti-server AuthType "ldap"

Configurare i parametri di connessione al server ldap esterno tramite i seguenti comandi: ::

    config setprop nethcti-server LdapBaseDN <BASE_DN>
    config setprop nethcti-server LdapOu <OU>
    config setprop nethcti-server LdapPort <LDAP_PORT>
    config setprop nethcti-server LdapServer <LDAP_SERVER>

Esempio: ::

    config setprop nethcti-server AuthType "ldap"
    config setprop nethcti-server LdapBaseDN "dc=mycompany,dc=local"
    config setprop nethcti-server LdapOu "Users"
    config setprop nethcti-server LdapPort "389"
    config setprop nethcti-server LdapServer "192.168.5.111"

Come ultima operazione eseguire: ::

    signal-event nethcti-server-update

Configurare l'autenticazione su Active Directory
================================================

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

