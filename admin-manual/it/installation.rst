=============
Installazione
=============

Per installare il server eseguire ::

  yum --enablerepo=nethupgrade install nethcti-server

Dall'interfaccia grafica di configurazione di |parent_product|, cliccare il pulsante "Applica cambiamenti", se presente.

Per installare il client eseguire ::

  yum --enablerepo=nethupgrade install nethcti

Aggiornamento dalla versione 2.x
================================

Per l'aggiornamento del server eseguire: ::

  yum --enablerepo=nethupgrade update nethcti-server

Per l'aggiornamento del client eseguire: ::

  yum --enablerepo=nethupgrade update nethcti

Aggiornamento dalla versione 1.x
================================

Per l'aggiornamento del server eseguire: ::

  service proxycti stop
  mkdir -p /home/e-smith/nethcti/backup
  mysqldump nethcti > /home/e-smith/nethcti/backup/nethcti.sql 2>/dev/null
  mysqldump asterisk > /home/e-smith/nethcti/backup/asterisk.sql 2>/dev/null
  rm -f /etc/nethcti/user_prefs.json /etc/nethcti/asterisk.json 2>/dev/null
  yum --enablerepo=nethupgrade update nethcti-server

Dall'interfaccia grafica di configurazione di |parent_product|, cliccare il pulsante "Applica cambiamenti", se presente.

Eseguire l'associazione :ref:`utenti-profili-interni telefonici <user_configuration_ref_label>` sempre attraverso la stessa interfaccia e cliccare nuovamente "Applica cambiamenti".

È possibile migrare il database dei dati con il seguente comando: ::

  /usr/lib/node/nethcti-server/docs/migratedb.js `config getprop nethcti-server DbPasswd`

Durante la fase di aggiornamento i dati del CTI (rubriche, postit, ecc) vengono convertiti automaticamente al nuovo formato.

La configurazione deve essere comunque rifatta a mano attraverso l'interfaccia grafica di |parent_product|.

Per l'aggiornamento del client eseguire: ::

  yum --enablerepo=nethupgrade update nethcti

