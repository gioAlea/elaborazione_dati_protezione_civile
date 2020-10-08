# elaborazione dati forniti dalla protezione civile relativi all'emergenza epidemiologica 2020

I dati sono riportati nello stesso formato con cui vengono forniti dalla protezione civile con l'aggiunta di tre colonne:

* 1) Colonna denominata "calcolo_nuovi_positivi": i valori sono calcolati con la seguente formula

calcolo_nuovi_positivi(i) = dimessi_guariti(i)-dimessi_guariti(i-1)+decessi(i)-decessi(i-1)+nuovi_positivi(i)

dove per i si intente la i-esima riga della tabella.

Per effettuare questo calcolo anche ai valori della prima riga, ho dovuto impostare delle ipotesi di valori iniziali, che sono le seguenti:

dimessi_guariti(0)=0,
decessi(0)=0

In altre parole, l'ipotesi è che al "giorno zero" i totali_positivi coincidano con le persone che al "giorno uno" vengono registrate come guarite e come decedute.

2) Si ha poi la colonna denominata "err_calcolo_variazione_totale_positivi" i cui valori sono calcolati con la seguente formula

* err_calcolo_variazione_totale_positivi(i) = calcolo_nuovi_positivi(i) - (dimessi_guariti(i)-dimessi_guariti(i-1)) - (decessi(i)-decessi(i-1)) - nuovi_positivi(i)

è la formula di cui sopra scritta bilanciando in maniera diversa i termini dalle due parti dell'uguale, in modo da esprimere la variabile dipendente in funzione di quelle indipendenti, a cui viene sottratto il valore fornito dalla protezione civile di nuovi_positivi(i) in modo da verificare che tra il dato calcolato a partire dall'identità matematica ed il dato fornito dalla prot.civ. non vi siano discrepanze

facendo le stesse ipotesi di condizioni iniziali, si osserva che calcolo_variazione_totale_positivi differisce da variazione_totale_positivi così come fornita dalla protezione civile 

3) Nella terza colonna err i dati sono calcolati come

* err(i) = calcolo_variazione_totale_positivi(i) - variazione_totale_positivi(i)

gli errori sembrano distribuiti in maniera piuttosto casuale, colpisce comunque quello più evidente al primo giorno, ossia nell'impostare le condizioni iniziali

nota: L'errore err(i) iniziale potrebbe  essere relativo sia alla variabile variazione_positivi(i) che alla variabile totale_positivi(i). questa ipotesi mi sembra che però sia smentita dal fatto che erro_calcolo_variazione_totale_positivi(i) sia sempre nullo.
