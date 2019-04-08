================================
QManager: Supervisore delle code
================================

QManager (QM) è l’applicazione sviluppata per il "Supervisore delle Code" e consente una gestione
completa di tutte le code del sistema in tempo reale e non.

Code
====

È possibile visualizzare ciascuna coda del sistema cliccando uno dei tabs presenti. Ogni tab mostra anche un
contatore per avere sempre sotto controllo il numero totale di chiamate in corso.
La pagina è suddivisa in due macro aree che riguardano le **chiamate** e gli **agenti in coda.**

Sezione #1: gestione delle chiamate
-----------------------------------

È possibile visualizzare in tempo reale l’elenco delle chiamate in **attesa** e di quelle **connesse** con i
relativi dettagli sul chiamante.

Subito sotto un grafico a barre mostra i tempi **minimi, massimi e medi** della
giornata corrente relativi alle chiamate in **attesa e connesse.**

Un altro grafico a torta mostra le percentuali di:

- chiamate fallite: non hanno ricevuto risposta e hanno atteso un tempo superiore ai 5 secondi
- chiamate processate: sono state risposte da un agente e quindi gestite correttamente
- chiamate nulle: non hanno ricevuto risposta e hanno atteso un tempo inferiore ai 5 secondi (solitamente il chiamante ha riattaccato praticamente subito, probabilmente per errore)

È possibile vedere il dettaglio delle percentuali fallite e processate cliccando il segmento relativo.
Il dettaglio delle processate visualizzerà quelle:

- processate entro il livello di servizio della coda (il default è pari a 1 minuto)
- processate dopo il livello di servizio della coda

Il dettaglio delle fallite visualizzerà quelle:

- per abbandono del chiamante
- per timeout
- per coda piena
- per aver premuto un pulsante relativo all’ascolto di un menù
- entrate in coda e fallite per l’assenza di agenti
- non entrate in coda per l’assenza di agenti

.. note:: I grafici vengono aggiornati automaticamente ogni 30 secondi.

Sezione #2: gestione degli agenti
---------------------------------

Un insieme di contatori riassume lo stato della coda, mostrando il numero degli agenti:

- in coda / fuori coda
- in pausa
- occupati in una conversazione transitata attraverso la coda
- occupati in una conversazione fuori dalla coda
- pronti a ricevere una chiamata dalla coda

Il supervisore può vedere in tempo reale lo stato di tutti gli agenti della coda e può interagire con ognuno di essi
attraverso le azioni mostrate nel menù contestuale.

Per ogni agente è anche possibile vedere sempre lo stato dell’interno telefonico e lo stato dell’agente stesso:

- verde: in coda
- grigio: fuori coda
- blu: sta gestendo una chiamata che ha attraversato la coda corrente
- arancio: sta gestendo una chiamata che ha attraversato un’altra coda
- rosso: sta gestendo una chiamata che non ha attraversato nessuna coda

Per ogni chiamata verrà mostrato anche l’identificativo dell’interlocutore e la direzione.

Realtime
========

Il tab *"Realtime"* mostra informazioni in tempo reale su tutte le code e agenti. È anche possibile eseguire determinate azioni.

Contatori
---------

Un insieme di contatori mostra un riepilogo di informazioni sulle chiamate e agenti di tutte le code:

- totale chiamate (in attesa e connesse)
- chiamate in attesa
- chiamate correntemente in gestione
- agenti in coda / fuori coda
- agenti in pausa
- agenti occupati
- agenti pronti a ricevere una chiamata

Statistiche code
----------------

Per ogni coda sono presenti due grafici, uno che mostra informazioni relative alle chiamate
(numero chiamate totali/in attesa/in gestione) e un altro relativo agli agenti (in coda/fuori coda/
in pausa/occupati/pronti a ricevere chiamate).

Statistiche agenti
------------------

Questa sezione visualizza informazioni relative agli agenti di tutte le code. Per ognuno di essi viene visualizzato:

- stato dell'interno telefonico
- stato dell'agente in coda
- orario dell'ultimo login in coda
- orario dell'ultimo logout dalla coda
- orario dell'ultimo ingresso in pausa
- orario di uscita dall'ultima pausa
- durata dell'ultimo intervallo di pausa eseguito
- numero di chiamate gestite
- orario dell'ultima chiamata gestita
- tempo intercorso dall'ultima chiamata gestita

Inoltre per ogni agente è possibile eseguire delle azioni cliccando il menù contestuale relativo.

Summary
=======

Il tab *"Summary"* mostra informazioni su tutte le code e agenti attraverso grafici interattivi e tabelle.
I dati all'interno del tab vengono aggiornati ogni 2 minuti se si resta sulla pagina e ogni volta che viene 
ricaricata la scheda oppure cambiata la tab.

Statistiche code
----------------

Nella parte superiore della pagina sono presenti 8 grafici all'interno dei quali vengono messe a confronto le code 
con la possibilità di disabilitarle tramite i pulsanti nella parte superiore della sezione.
Ogni coda ha associato un colore che persiste all'interno di tutti i grafici. Per ogni grafico è presente 
un'icona la quale fa comparire la spiegazione del grafico.

I dati rappresentati nel grafico sono:

- chiamate totali: numero di chiamate entrate per ogni coda e percentuale sulle chiamate totali del giorno
- chiamate processate: numero di chiamate processate per ogni coda e percentuale sulle chiamate totali entrate in coda
- chiamate processate prima del livello di servizio: numero di chiamate processate prima del livello di servizio per ogni coda e percentuale sulle chiamate totali entrate in coda
- chiamate fallite: numero di chiamate non riuscite per ogni coda e percentuale sulle chiamate totali entrate in coda
- chiamate invalide: numero di chiamate non valide per ogni coda e percentuale sulle chiamate totali entrate in coda
- ragioni chiamate fallite: chiamate non riuscite per i seguenti motivi: abbandono, code piena, timeout, nessuno all'ingresso in coda, nessun agente in coda e con ivr per ogni coda
- chiamate in attesa: durata minima, media e massima delle chiamate in attesa per ogni coda
- durata chiamate: durata chiamate minima, media e massima per ogni coda

Statistiche agenti
------------------

Nella sezione inferiore della pagina sono presenti i dati relativi agli agenti e alle code per ogni agente oltre allo stato dell'agente e dell'agente in ogni coda.
Gli agenti possono essere filtrati e ordinati per nome e interno.

Le tabelle contenenti i dati di ogni agente sono divise in macroaree secondo il seguente schema:

Login:

- ultimo login
- ultimo logout

Chiamate:

- chiamate risposte
- chiamate in uscita
- chiamate non risposte
- da ultima chiamata (tempo trascorso dall'ultima chiamata)
- tempo al telefono (tempo totale trascorso al telefono)

Lunghezza chiamate:

- min (durata minima delle chiamate)
- max (durata massima delle chiamate)
- media (durata media delle chiamate)
- totale in ingresso (durata totale delle chiamate in ingresso)
- totate in uscita (durata totale delle chiamate in uscita)

Sotto le tabelle che mostrano le informazioni degli agenti si trova la lista delle code alle quali l'agente appartiene con le relative tabelle contenenti
le informazioni dell'agente riferite alla coda.

I dati visualizzati per ogni coda sono:

- in coda (tempo trascorso in coda)
- tempo in pausa
- pausa su logon (percentuale del tempo in pausa rispetto al tempo trascorso in coda)
- tempo al telefono

Accanto al nome di ogni coda è presente lo stato dell'agente in coda e alla sinistra di ogni avatar nella parte alta della card è presente lo stato telefonico

Monitor
=======

Il tab «Monitor» mostra in tempo reale le chiamate in attesa nelle code abilitate.

Nella sezione superiore è presente la lista delle code con la possibilità di abilitarle oppure disabilitarle e una select che permette di selezionare il numero di chiamate da mostrare.

Le chiamate in attesa vengono mostrate in formato tabellare mostrando le seguenti informazioni:

- nella prima colonna è presente un cerchio colorato in base alla presenza oppure no di una chiamata in attesa nella medesima posizione (verde se la posizione è libera, rosso se la posizione è occupata)
- nella seconda colonna viene mostrato il chiamante
- nella terza colonna viene mostrata la posizione della chiamata
- nella quarta colonna viene mostrato da quanto tempo la chiamata è in attesa

Nella parte superiore destra di ogni tabella è presente un'icona che permette di invertire i colori nella tabella in base alla preferenze.
