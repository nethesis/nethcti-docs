================================
QManager: Supervisore delle code
================================

QManager (QM) è l’applicazione sviluppata per il "Supervisore delle Code" e consente una gestione
completa di tutte le code abilitate.

Dashboard
=========

Offre una visione d'insieme delle attività avvenute durante la giornata con classifiche, dati e grafici.

È possibile suddividere la Dashboard in 4 sezioni:

Sezione #1: Allarmi
-----------------------------------

Nella parte superiore è presente la sezione degli allarmi all'interno della quale vengono visualizzati gli allarmi specifici per ogni coda.

Gli allarmi possono essere:

- numero di agenti insufficiente (il rapporto tra il numero di chiamate in attesa e il numero di agenti ha superato la soglia di allarme)
- tempo di attesa medio elevato (il tempo di attesa medio ha superato la soglia di allarme)
- carico elevato (ci sono molte chiamate in attesa e il tempo medio di attesa ha superato la soglia di allarme)
- numero elevato di chiamate in attesa (ci sono molte chiamate in attesa e la prima chiamata è in attesa da molto tempo)

Ogni messaggio d'allarme è accompagnato dall'ora d'inizo, dalla coda alla quale corrisponde e da una spiegazione più dettagliata visualizzata tramite tooltip.

Appena viene rilevato un'allarme viene visualizzata:

- una notifica desktop con il messaggio dell'allarme
- il messaggio nella sezione Allarmi della Dashboard
- il messaggio tra gli allarmi relativi alla specifica installazione su my.nethesis.it

.. note:: I messaggi d'allarme sia su my.nethesis.it che nella Dashboard vengono visualizzati fino alla risoluzione della criticità.

Sezione #2: Grafici
-----------------------------------

Delle sezione Grafici fanno parte, partendo dalla parte alta della pagina:

- i grafici per i totali che indicano l'andamento delle:

1) chiamate totali
2) chiamate risposte
3) chiamate non risposte
4) chiamate invalide

- il grafico della distribuzione oraria delle chiamate entrate divise per coda
- il grafico della distribuzione oraria delle chiamate risposte divise per coda
- il grafico della distribuzione oraria delle chiamate non risposte divise per coda

Nei grafici vengono mostrati i dati a partire da 30 minuti prima della prima chiamata in entrata.

Per tutti i grafici l'intervallo temporale sull'asse x e l'aggiornamento dei dati mostrati sono impostati a 30 minuti.

Apparte i grafici dei totali i quali indicano solemante l'andamento, nei restanti grafici è possibile visualizzare le informazioni nel rispettivo momento per singola coda andandoci sopra con il puntatore del mouse.

Sezione #3: Classifiche agenti
-----------------------------------

Al di sotto rispetto al grafico della distribuzione oraria delle chiamate entrate sono presenti le classifiche degli agenti per:

- chiamate risposte (classifica agenti per chiamate riposte per coda)
- chiamate non risposte (classifica agenti per chiamate non risposte per coda)
- percentuale pausa su logon (classifica agenti per percentuale di pausa su logon per coda)
- tempo in login (classifica agenti per tempo di login per coda)
- tempo in pausa (classifica agenti per tempo di pausa per coda)
- percentuale tempo in chiamata (classifica agenti per percentuale di tempo in chiamata per coda)

I dati delle classifiche degli agenti diversamente dai grafici vengono aggiornati ogni 30 secondi oppure al caricamento della pagina e sono in tempo reale.

Le posizioni in classifica dipendono dalle singole code delle quali lo specifico agente fa parte, ciò comporta il fatto che un agente possa occupare più di una posizione nella classifica ma per code diverse.

Il numero di posizioni da visualizzare per ogni classifica è impostato a 5.

Sezione #4: Classifiche code
-----------------------------------

In corrispondenza e sottostanti al grafico della distribuzione delle chiamate risposte per coda sono presenti le classifice delle code per:

- chiamate risposte (classifica delle code per chiamate risposte)
- chiamate totali (classifica delle code per chiamate totali)
- chiamate non risposte (classifica delle code per chiamate non risposte)
- chiamate invalide (classifica delle code per chiamate invalide)
- motivazioni di chiamata non risposta (classifica delle code per motivazioni di chiamata non risposta)

Diversamente dalle classifiche degli agenti il numero delle code non viene limitato in nessun modo, mostrando i dati di tutte le code abilitate per il QM.

I dati mostrati nelle classifiche delle code vengono aggiornati ogni 30 secondi come nelle classifiche per agenti oppure al caricamento della pagina e vengono aggiornate in tempo reale.

------------

Situati alla destra rispetto ai titoli di ogni classifica sono presenti 2 icone:

- la prima per invertire l'ordine delle posizioni all'interno delle classifiche e mostrare le code oppure gli agenti peggiori e viceversa
- la seconda per aprire un tooltip contenente una spiegazione più esaustiva della classifica in questione

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

Chiamate perse
==============

Il tab *"Chiamate perse"* mostra informazioni sulle chiamate perse nelle code appartenenti al QM. Per ogni chiamata è anche possibile eseguire alcune azioni.

Nella parte superiore del tab sono presenti le informazioni relative all'intervallo di aggiornamento delle informazioni sulle chiamate perse.
L'intervallo di aggiornamento è anche un link alla pagina delle impostazioni dell'agente da dove è possibile cambiare l'intervallo di aggiornamento delle chiamate 
perse sia per la pagina "Code" che per la pagina "Chiamate perse" del QM.

Sottostante all'intervallo di aggiornamento è presente un pulsante tramite il quale è possibile esportare in formato CSV tutte le chiamate perse.

Le informazioni relative alle chiamate perse vengono mostrate in formato tabellare e si dividono in "Non gestite", "Gestite" e "Tutte".
Ogni tabella è composta dalle seguenti colonne:

- Ora: data e ora in cui è avvenuta la chiamata
- Coda: il nome e il numero della coda nella quale è entrata la chiamata
- Azienda: se presente il nome dell'azienda
- Nome: se presente il nome del contatto in rubrica
- Chiamante: il numero del chiamante
- Info: pulsante che permette di visualizzare il percorso completo compiuto dalla chiamata tramite una seconda tabella
- Stato: se si tratta di una chiamata in uscita oppure in entrata
- Esito: se la chiamata è stata gestita oppure non gestita
- Azioni: se la chiamata non è stata gestita è presente un pulsante che permette di selezionare un agente della coda connesso in chat e inviare un messaggio automatico con informazioni utili per richiamare il contatto

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

Accanto al nome di ogni coda è presente lo stato dell'agente in coda e alla sinistra di ogni avatar nella parte alta della card è presente lo stato telefonico.

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
