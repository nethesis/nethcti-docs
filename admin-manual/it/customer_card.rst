=============
Customer card
=============

Con il termine *customer card* si indica un insieme di informazioni che
il server fornisce ai client |product| ogni volta che si riceve una
chiamata o che si fa click su un elemento della rubrica.

Una customer card è costituita da due parti fondamentali:

-  una :dfn:`query` su un database locale o remoto
-  un :dfn:`template` per il rendering dei risultati della query

La configurazione di default fornisce già le seguenti customer card:

-  dettagli anagrafici dalla rubrica centralizzata
-  ultime 10 chiamate associate al cliente

Altri esempi comuni di customer card sono:

-  ticket di assistenza associati al cliente
-  insoluti e stato pagamenti
-  dettagli anagrafici da gestionale
-  trattative, contratti e altre informazioni estratte da crm

Le customer cards possono essere configurate attraverso l'interfaccia
tradizionale di |parent_product| accedendo alla sezione "CTI". Una volta create è possibile abilitarne i permessi relativi tramite la configurazione dei profili utente.

Query
=====

Attualmente sono supportati due tipi di database:

-  MySQL
-  Microsoft SQL Server

Ogni query è composta dai seguenti campi:

-  **Nome**: è il nome della customer card, deve essere diverso da
   quello di altre customer card salvate. *identity* e *calls* sono nomi
   riservati alle customer card di default. Il nome della customer card
   NON può contenere il carattere **"\_"**.
-  **Tipo di database**: è il tipo di database dove verrà effettuata la
   query
-  **Porta Database**: è la porta usata per raggiungere il database. Nel
   caso di database locale su Nethservice è possibile utilizzare il
   socket unix */var/lib/mysql/mysql.sock*
-  **Host**: è l'host che ospita il database
-  **Query**: è la query da eseguire. La parola chiave :dfn:`$EXTEN` verrà sostituita con il numero telefonico su cui effettuare la ricerca.

.. note:: Se si utilizza il carattere "\\", ad esempio nel nome del database, è necessario farlo precedere dal carattere di escape "\\". Esempio: se il nome del database è "TEST\\SQLEXPRESS" allora il nome corretto da inserire è "TEST\\\\SQLEXPRESS".

**Esempio query**

L'esempio seguente crea una customer card "ticket" che, all'arrivo di
una chiamata, mostra nel cti i risultati di una query effettuata sul
database di otrs:

====================== ====================================================================================
**Nome**               ticket
**Nome Visualizzato:** ticket
**Tipo di database**   mysql
**Porta Database**     /var/lib/mysql/mysql.sock
**Nome Database**      otrs
**Database Username**  otrs
**Database Password**  \*\*\*
**Query**              SELECT T.title AS Titolo, date\_format(T.create\_time,'%d/%m/%Y %H:%i') AS c\_time,\
                       date\_format(T.change\_time,'%d/%m/%Y %H:%i') AS m\_time, CONCAT(U.first\_name,' ',\
                       U.last\_name) AS gestore, 'Cliente', TS.name AS stato FROM ticket T INNER JOIN \
                       customer\_user CU ON T.customer\_user\_id=CU.login INNER JOIN ticket\_state TS ON \
                       T.ticket\_state\_id=TS.id INNER JOIN users U ON T.change\_by=U.id WHERE (CU.phone \
                       LIKE '%$EXTEN%') LIMIT 10
====================== ====================================================================================


Template
========

Dopo aver configurato la query, è necessario creare un template per
effettuare il rendering del risultato. Tutti i template devono essere
salvati nella directory */var/lib/nethserver/nethcti/templates/customer_card*.

Il nome del file di ciascun template deve essere nella forma:

``decorator_cc_``\ ``<numero_ordinale>``\ ``_``\ ``<nome_customer_card>``\ ``.ejs``

Il *numero\_ordinale* serve per decidere l'ordine di visualizzazione del
template e deve essere diverso da "00" e "20" che sono riservati per le due
customer cards di default: "anagrafica" e "ultime chiamate" rispettivamente.
Il *nome\_customer\_card* deve coincidere con il nome deciso durante la
configurazione della query.

Esempi di nomi di file:

::

 decorator_cc_25_insoluti.ejs
 decorator_cc_35_trattative.ejs


I template utilizzano la sintassi **ejs** che, in modo del tutto simile
a quello che avviene in PHP, permettono di "immergere" codice javascript
all'interno di una pagina html e di generare in output un documento (o
un frammento) html interpretabile dai browser. |product| fornisce già una
lista di esempi pronti all'uso nella directory
**/usr/lib/node/nethcti-server/docs/custcard_examples**:

-  **base\_table.ejs**: visualizza una tabella molto semplice contenente
   tutte le colonne e le righe del risultato della query
-  **beautiful\_table.ejs**: come base\_table.ejs ma applica un css alla
   tabella
-  **manual\_table.ejs**: visualizza una tabella contenente tutte le le
   righe del risultato della query, ma le colonne visualizzate devono
   essere specificate manualmente
-  **one\_result.ejs**: visualizza le prime due colonne del primo
   risultato della query

Se ad esempio si vuole creare una tabella di visualizzazione per la
query sui ticket vista nel paragrafo precedente, eseguire:

::

 cp /usr/lib/node/nethcti-server/docs/custcard_examples/beautiful_table.ejs /var/lib/nethserver/nethcti/templates/customer_card/decorator_cc_30_ticket.ejs
 signal-event nethcti-server-update

Risultati
---------

All'interno di ogni template è automaticamente disponibile la variabile
**results**, un array che contiene tutti i risultati della query. Per inserire
delle immagini all'interno del template è sufficiente usare il path:

::

 /webrest/static/img/<FILENAME>

e inserire il file nel path relativo:

::

 /var/lib/nethserver/nethcti/static/img/<FILENAME>

Si consiglia di creare una sottodirectory per la specifica customer card, ad esempio:

::

 /var/lib/nethserver/nethcti/static/img/ticket/<FILENAME>

Ogni riga dell'array results è nel formato:

::

 ( colonna1 => valore1, colonna2 => valore2 ... colonnaX => valoreX )

Ad esempio, data una query del tipo:

::

 SELECT nome, cognome, tipo FROM rubrica

Con risultato:

::

  mario,rossi,azienda
  giuseppe,bianchi,privato

L'array avrà il formato:

::

   [0] => { nome: "mario", cognome: "rossi", tipo: 'azienda' }
   [1] => { nome: "giuseppe", cognome: "bianchi", tipo: 'privato' }

Quindi, per accedere ad esempio al cognome del secondo risultato:

::

 results[1].cognome        // ritornerà "bianchi"

All'interno della variabile **results.length** è contenuto il numero dei
risultati ottenuti.

Sintassi
--------

I template ejs utilizzano la sintassi standard di javascript.

Per inserire codice all'interno di un frammento html, si usano i tag:

::

 <% ...codice... %>

Se si desidera stampare direttamente il valore di una variabile, si può
usare il formato:

::
 
 <%= nome_variabile %>

Riportiamo un paio di esempi riprendendo la query vista nel paragrafo
precedente.

Stampa il primo risultato:

::

 Nome: <%= result[0].nome %>
 Cognome: <%= result[0].cognome %>
 Tipo: <img src='/webrest/static/img/web.png' />

Output:

::

 Nome: mario
 Cognome: rossi
 Tipo:  <img src='/webrest/static/img/web.png' />

Stampa tutti i risultati:

::

  <% for (var i = 0; i < results.length; i++) { %>
      Nome:  <%= results[i].nome %>
      Cognome: <%= results[i].cognome %>
  <% } %>

Per ulteriori dettagli sulla sintassi di ejs, consultare:

-  https://github.com/visionmedia/ejs
-  https://developer.mozilla.org/it/docs/JavaScript
