# elaborazione dati forniti dalla protezione civile relativi all'emergenza epidemiologica 2020
elaborazione dati forniti dalla protezione civile in merito alla pandemia

I dati sono riportati nello stesso formato con cui vengono forniti dalla protezione civile con l'aggiunta di tre colonne:


calcolo_nuovi_positivi(i) = dimessi_guariti(i)-dimessi_guariti(i-1)+decessi(i)-decessi(i-1)+nuovi_positivi(i)

condizioni iniziali: dimessi_guariti(0)=0, decessi(0)=0 - in altre parole: al giorno zero, i positivi sono le persone che al giorno 1 vengono registrate come guarite e come decedute

calcolo_variazione_totale_positivi(i) = nuovi_positivi(i) - (dimessi_guariti(i)-dimessi_guariti(i-1)) - (decessi(i)-decessi(i-1))

è la formula di cui sopra scritta bilanciando in maniera diversa i termini dalle due parti dell'uguale, in modo da esprimere la variabile dipendente in funzione di quelle indipendenti

facendo le stesse ipotesi di condizioni iniziali, si osserva che calcolo_variazione_totale_positivi differisce da variazione_totale_positivi così come fornita dalla protezione civile 

err(i) = calcolo_variazione_totale_positivi(i) - variazione_totale_positivi(i)

gli errori sembrano distribuiti in maniera piuttosto casuale, colpisce comunque quello più evidente al primo giorno, ossia nell'impostare le condizioni iniziali
