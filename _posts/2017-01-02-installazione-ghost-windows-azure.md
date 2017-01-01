---
layout: post
title: Installazione della piattaforma blog Ghost in Windows Server 2016 su Azure
---
Una piattaforma per il blog che mi aveva interessato molto prima di scoprire [GitHub Pages](https://pages.github.com/) è [Ghost](): mi era piaciuto il design abbastanza minimale ma pulito dell'interfaccia utente; ho provato ad installarlo su una macchina virtuale in Azure con Windows Server 2016, per capire se fosse una operazione complicata: diciamo che con qualche accortezza e un suggerimento di google sono riuscito ad ottenere una base funzionante.
Anche se ho scelto di utilizzare `GitHub Pages` come base per i miei post, mi riprometto di utlizzare `Ghost` per un altro blog che vorrei curare, incentrato su `Nano Server`..ma come si dice..questa è un'altra storia.

Vi illustro per chi fosse interessato i passi che ho seguito per l'installazione di `Ghost` nella configurazione accennata prima.

## Setup Windows Server 2016 su Azure

## Setup di Node.js

1. Andare alla pagina [Node.js Download](http://nodejs.org/en/download) e cliccare su `Windows Download`

   ![Download Node.js LTS](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-01.png)

2. Una volta scaricato l'installer, cliccare per iniziare l'esecuzione

   ![Installa Node.js](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-02.png)

3. Come in tutti i programmi di installazione Windows, vi sarà richiesto in sequenza

      i. Accettare i termini di licenza del software

      ![Node.js licenza](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-04.png)

      ii. Scegliere la directory di installazione

      ![Node.js directory installazione](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-05.png)

      iii. Scegliere le componenti da installare (di default, tutte)

      ![Node.js componenti installazione](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-06.png)

      iv. Confermare cliccando sul tasto `Install`
 
      ![Node.js conferma installazione](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-03.png)

      v. Aspettare che il Node.js si installi

      ![Node.js aspettare installazione](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-03.png)

      vi. Completare l'installazione cliccando sul tasto `Finish`

      ![Node.js conclusione installazione](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-03.png)
      
## Installazione di Ghost

1. Andare alla pagina [Ghost Download](http://ghost.org/developers) e cliccare su `Download Ghost`.

   ![Download Ghost](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Pages-Intro-01.png)

2. Creare sul filesystem una directory `C:\Ghost` dove verrà estratto il contenuto del file zip scaricato dal sito `Ghost` nel passo precedente.

   ![Ghost estrazione in directory](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Pages-Intro-02.png)

3. Andare su `Start`, individuare la cartella `Node.js` e cliccare su `Node.js command prompt`.

   ![Node.js command prompt](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Pages-Intro-03.png)

4. Nella command prompt cambiare directory in modo da puntare la directory di installazione di `Ghost` e lanciare il comando di installazione.

   ```nodejs
   cd \Ghost
   npm install production
   ```

5. L'installazione dura dai 5 ai 10 minuti.

   ![Ghost installazione](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-08.png)

## Setup di Ghost

1. Avviare `Ghost` 

   ```nodejs
   npm Start
   ```

   ![Ghost avvio piattaforma](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Theme-01.png)

2. Nel browser basta digitare `http://127.0.0.1:2368/` per vedere la pagina iniziale generica del blog.

   ![Ghost pagina iniziale](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Theme-02.png)

3. Per il setup, cliccare su `http://127.0.0.1:2368/ghost` e in sequenza

      i. Cliccare su `Create account`

      ![Ghost creazione account](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-04.png)

      ii. Inserire indirizzo mail, password per l'accesso all'interfaccia di amministrazione e titolo del blog

      ![Ghost credenziali](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-05.png)

      iii. Inserire persone che partecipino alla gestione del blog (se non si vuole fare in questo momento, cliccare su `I'll do this later, take me to my blog`)

      ![Ghost team](/img/2016-12-30/GitHub-Desktop-Installation/GitHub-Desktop-Installation-06.png)

4. Appare l'interfaccia per la gestione del blog e la scrittura dei post.

   ![Ghost gestione e creazione post](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Commit.png)

Date uno sguardo adesso al blog cliccando sul link `http://127.0.0.1:2368/`

   ![Ghost blog](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Commit.png)

e poi sul post di esempio

   ![Ghost post esempio](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Commit.png)

Per ora stiamo facendo tutto in un browser locale sulla macchina virtuale: e se volessimo aprire il nostro blog da qualsiasi altra parte?
Ovviamente si può fare, facendo qualche configurazione lato Azure e una lato Node.js/Ghost.

## Configurazione Azure

Per avere accesso al blog dall'esterno della macchina virtuale dobbiamo settare un `nome dns` ed aprire una porta nel `Security Group` al quale appartiene la macchina virtuale.

1. Nell'interfaccia di Azure, selezionare la macchina virtuale sulla quale abbiamo installato `Ghost`.

   ![Azure server Ghost](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

2. Andare in alto a sinistra e cliccare sull'icona che rappresenta i `Resource groups`.

   ![Azure Resource groups](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

3. Cliccare sul `Resource group` che in fase di installazione della macchina virtuale le avevamo assegnato (nel nostro caso `Ghost`).

   ![Azure selezione Resource group](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

4. Andare sulla voce che rappresenta il `Public IP address` (nel nostro caso `svr-ghost-ip`).

   ![Azure IP pubblico](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

5. Andare sulla voce `Configuration`

   ![Azure Configurazione dns](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

6. In `DNS name label` inserire un nome che utilizzeremo per richiamare da browser il nostro blog (nel caso di esempio, il nome scelto è `nanoserver4all`); una volta inserito il nome, se premete il tasto `TAB` sulla tastiera verificate se il nome è univoco nel DNS Microsoft oppure se dovete cambiarlo. Se è tutto ok, salvate cliccando in alto su `Save`.

   ![Azure nome dns](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

7. Andare alla voce che rappresenta il `Network security group` (nel nostro caso `svr-ghost-nsg`)

   ![Azure network security group](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

8. Cliccare su `Inbound security rules` sotto l'etichetta `SETTINGS`.

   ![Azure Inbound security rules](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

9. Nell'interfaccia che si apre cliccare su `Add`, configurando la regola con i seguenti parametri e premendo `OK` alla fine della configurazione.

   * Name = default-allow-ghost-test
   * Priority = 1010
   * Source = Any
   * Service = Custom
   * Protocol = TCP
   * Port range = 2368
   * Action = Allow

   ![Azure configurazione parametri regola inbound](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

10. La tabella delle regole inbound dovrebbe presentarsi dopo qualche istante in questo modo.

   ![Azure lista regole inbound](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

A questo punto avevo pensato di aver completato tutto: vado a fare una prova ed ottengo un errore di connessione rifiutata; all'inizio ho pensato che fosse il firewall di Windows a bloccare la comunicazione, ma anche disattivandolo il risultato era lo stesso. Ho analizzato anche con Wireshark ma sinceramente non riuscivo a capire: ho pensato che nella comunicazione si vedesse la rete interna e che quindi i pacchetti andasseto persi..ma non era neanche quella la soluzione.
Per farla breve, cercando su google ho trovato che nel file di configurazione di `Ghost`, `config.js`, l'ip che viene puntato è sempre quello locale, `127.0.0.1` e quindi qualsiasi chiamata verso un altro indirizzo che non sia quello non viene presa in considerazione; per ovviare a questa situazione, basta cambiare nella parte del file indicata come `development` l'host del server, facendolo puntare a `0.0.0.0`

```javascript
   host: `0.0.0.0`,
```

   ![config.js punta a tutti gli indirizzi](/img/2016-12-30/GitHub-Pages-Intro/GitHub-Sito-01.png)

Riavviando `Ghost`, collegandoci da un browser esterno otteeniamo il nostro blog.

Mi sono dilungato molto nella spiegazione, a volte per dei tecnici molte cose potrebbero sembrare scontate, ma magari qualcuno che non ha alcuna conoscenza trova questo post e riesce ad installare e fare una prova con `Ghost`.

Nel prossimo post vi mostrerò invece come caricare `Ghost` come web app su `Azure`, cosa che dovrebbe essere molto più veloce e immediata rispetto a quanto visto.

