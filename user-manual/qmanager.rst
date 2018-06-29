================================
QManager: Supervisore delle code
================================

QManager (QM) è l’applicazione sviluppata per il "Supervisore delle Code" e consente una gestione
completa di tutte le code del sistema in tempo reale e non.

Versione
========

L’applicazione è correntemente in versione Beta e ci rimarrà fino al raggiungimento del “feature-parity”
con la vecchia versione queueman.

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