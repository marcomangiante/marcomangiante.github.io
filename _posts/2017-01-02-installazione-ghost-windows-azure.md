---
layout: post
title: Installazione della piattaforma blog Ghost in Windows Server 2016 su Azure
---
Una piattaforma per il blog che mi aveva interessato molto prima di scoprire [GitHub Pages](https://pages.github.com/) è [Ghost](): mi era piaciuto in particolare il design minimale ma pulito dell'interfaccia utente. 

Ho provato ad installarlo su una macchina virtuale in Azure con Windows Server 2016, per capire se fosse una operazione complicata: diciamo che con qualche accortezza e un suggerimento di google sono riuscito ad ottenere una base funzionante.

Anche se ho scelto di utilizzare GitHub Pages come base per i miei post, mi riprometto di utlizzare Ghost per un altro blog che vorrei curare, incentrato su `Windows Server 2016 - Nano Server`..ma come si dice..questa è un'altra storia.

Vi illustro per chi fosse interessato i passi che ho seguito per l'installazione di Ghost nella configurazione accennata prima.

## Setup Windows Server 2016 su Azure

1. Una volta connessi al [portale di Azure](http://portal.azure.com) andare sull'icona `Virtual machines`.

   ![Azure Virtual Machines](/img/2017-01-02/Ghost/azure-01.png)

2. Cliccare su `Add`.

   ![Azure aggiungere una virtual machine](/img/2017-01-02/Ghost/azure-02.png)

3. Nella schermata che appare, selezionare l'immagine che indica `Windows Server`.

   ![Azure selezione Windows Server](/img/2017-01-02/Ghost/azure-03.png)

4. Scorrere la lista e selezionare `Windows Server 2016 Datacenter`. 

   ![Azure selezione Windows Server 2016 Datacenter](/img/2017-01-02/Ghost/azure-04.png)

5. Nella schermata che appare cliccare su `Create`.

   ![Azure scelta tipo deployment](/img/2017-01-02/Ghost/azure-05.png)

6. Viene richiesto di inserire i dati di base per la creazione della virtual machine; i parametri da valorizzare sono

   * Name - Nome che daremo alla virtual machine
   * VM disk type - tipo di disco che vogliamo utilizzare tra HDD e SSD
   * Username - nome utente dell'account che utilizzeremo per fare l'accesso alla virtual machine
   * Password - password dell'account che utilizzeremo per fare l'accesso alla virtual machine
   * Confirm password - stessa password inserita prima
   * Subscription - si sceglie la sottoscrizione alla quale legare la virtual machine e i suoi costi
   * Resource group -  viene richiesto se crearne uno nuovo oppure utilizzarne uno creati in precedenza

   ![Azure creazione vm dati base](/img/2017-01-02/Ghost/azure-06.png)

7. Una volta inseriti questi dati per la crezione della vm, viene presentata una schermata nella quale vengono suggeriti 3 tipi di virtual machine da scegliere; se si è interessati ad una delle 3, basta cliccarci sopra e quindi cliccare su
 `Select`.

   ![Azure scelta vm default](/img/2017-01-02/Ghost/azure-07.png)

8. Se invece si vuole scegliere un altro tipo di virtual machine, basta cliccare su `View All`, cercarla, selezionarla e cliccare su `Select`. 

   ![Azure scelta vm](/img/2017-01-02/Ghost/azure-08.png)

9. Compare la schermata dove è possibile scegliere alcune caratteristiche, per esempio, dello storage, extension, etc..per ora lasciate tutto di default e cliccate su `OK`.

   ![Azure scelta opzioni sistema vm](/img/2017-01-02/Ghost/azure-09.png)

10. A questo punto, vengono riepilogate le scelte fatte in precedenza: se è tutto come avete scelto basta cliccare su `OK` e Azure inizierà a creare la vostra virtual machine.

   ![Azure creazione vm](/img/2017-01-02/Ghost/azure-10.png)

## Setup di Node.js

1. Andare alla pagina [Node.js Download](http://nodejs.org/en/download) e cliccare su `Windows Download`.

   ![Download Node.js LTS](/img/2017-01-02/Ghost/Ghost-01.png)

2. Una volta scaricato l'installer, cliccare su `Next `per iniziare l'esecuzione.

   ![Installa Node.js](/img/2017-01-02/Ghost/Ghost-02.png)

3. Come in tutti i programmi di installazione Windows, vi sarà richiesto in sequenza di

      i. Accettare i termini di licenza del software.

      ![Node.js licenza](/img/2017-01-02/Ghost/Ghost-03.png)

      ii. Scegliere la directory di installazione.

      ![Node.js directory installazione](/img/2017-01-02/Ghost/Ghost-04.png)

      iii. Scegliere le componenti da installare (di default, tutte).

      ![Node.js componenti installazione](/img/2017-01-02/Ghost/Ghost-05.png)

      iv. Confermare cliccando sul tasto `Install`.
 
      ![Node.js conferma installazione](/img/2017-01-02/Ghost/Ghost-06.png)

      v. Aspettare che il Node.js si installi.

      ![Node.js aspettare installazione](/img/2017-01-02/Ghost/Ghost-07.png)

      vi. Completare l'installazione cliccando sul tasto `Finish`.

      ![Node.js conclusione installazione](/img/2017-01-02/Ghost/Ghost-08.png)
      
## Installazione di Ghost

1. Andare alla pagina [Ghost Download](http://ghost.org/developers) e cliccare su `Download Ghost`.

   ![Download Ghost](/img/2017-01-02/Ghost/Ghost-09.png)

2. Creare sul filesystem una directory `C:\Ghost` dove verrà estratto il contenuto del file zip scaricato dal sito nel passo precedente.

   ![Ghost estrazione in directory](/img/2017-01-02/Ghost/Ghost-10.png)

3. Andare su `Start`, individuare la cartella `Node.js` e cliccare su `Node.js command prompt`.

   ![Node.js command prompt](/img/2017-01-02/Ghost/Ghost-11.png)

4. Nella command prompt cambiare directory in modo da puntare quella di installazione di Ghost e lanciare il comando di installazione.

   ```javascript
   cd \Ghost
   npm install --production
   ```
   ![Ghost inizio installazione](/img/2017-01-02/Ghost/Ghost-12.png)

5. L'installazione dura dai 5 ai 10 minuti.

   ![Ghost installazione](/img/2017-01-02/Ghost/Ghost-13.png)

## Setup di Ghost

1. Avviare Ghost con il comando 

   ```js
   npm Start
   ```
   ![Ghost avvio piattaforma](/img/2017-01-02/Ghost/Ghost-14.png)

2. Nel browser basta digitare `http://127.0.0.1:2368/` per vedere la pagina iniziale generica del blog.

   ![Ghost pagina iniziale](/img/2017-01-02/Ghost/Ghost-15.png)

3. Per il setup, cliccare su `http://127.0.0.1:2368/ghost` e in sequenza

      i. Cliccare su `Create Your Account`.

      ![Ghost creazione account](/img/2017-01-02/Ghost/Ghost-16.png)

      ii. Inserire indirizzo mail, password per l'accesso all'interfaccia di amministrazione e titolo del blog.

      ![Ghost credenziali](/img/2017-01-02/Ghost/Ghost-17.png)

      iii. Inserire persone che partecipino alla gestione del blog (se non si vuole farlo in questo momento, cliccare su `I'll do this later, take me to my blog`).

      ![Ghost team](/img/2017-01-02/Ghost/Ghost-18.png)

4. Appare l'interfaccia di amministrazione per la gestione del blog e la scrittura dei post.

   ![Ghost gestione e creazione post](/img/2017-01-02/Ghost/Ghost-19.png)

Date uno sguardo adesso al blog cliccando sul link `http://127.0.0.1:2368/` noterete che è cambiato il titolo del blog.

   ![Ghost blog](/img/2017-01-02/Ghost/Ghost-20.png)

Per dare uno sguardo a come si presentano i post, cliccate su quello di esempio.

   ![Ghost post esempio](/img/2017-01-02/Ghost/Ghost-21.png)

Per ora stiamo facendo tutto in un browser locale sulla macchina virtuale: e se volessimo vedere il nostro blog da qualsiasi altro device?

Ovviamente si può fare, facendo qualche configurazione lato Azure e una lato Node.js/Ghost.

## Configurazione Azure

Per avere accesso al blog dall'esterno della macchina virtuale dobbiamo settare un `nome dns` ed aprire una porta nel `Security Group` al quale appartiene la macchina virtuale.

1. Nell'interfaccia di Azure, selezionare la macchina virtuale sulla quale abbiamo installato Ghost.

   ![Azure server Ghost](/img/2017-01-02/Ghost/azure-11.png)

2. Andare in alto a sinistra e cliccare sull'icona che rappresenta i `Resource groups`.

   ![Azure Resource groups](/img/2017-01-02/Ghost/azure-12.png)

3. Cliccare sul `Resource group` che in fase di installazione della macchina virtuale le avevamo assegnato (nel nostro caso `Ghost`).

   ![Azure selezione Resource group](/img/2017-01-02/Ghost/azure-13.png)

4. Andare sulla voce che rappresenta il `Public IP address` (nel nostro caso `svr-ghost-ip`) e cliccarci sopra.

   ![Azure IP pubblico](/img/2017-01-02/Ghost/azure-14.png)

5. Cliccare sulla voce `Configuration`.

   ![Azure Configurazione dns](/img/2017-01-02/Ghost/azure-15.png)

6. In `DNS name label` inserire un nome che utilizzeremo per richiamare da browser il nostro blog (nel caso di esempio, il nome scelto è `nanoserver4all`); una volta inserito il nome, se premete il tasto `TAB` sulla tastiera verificate se il nome è univoco nel DNS Microsoft oppure se dovete cambiarlo. 
Se è tutto ok, salvate cliccando in alto su `Save`.

   ![Azure nome dns](/img/2017-01-02/Ghost/azure-16.png)

7. Andare a cliccare sulla voce che rappresenta il `Network security group` (nel nostro caso `svr-ghost-nsg`).

   ![Azure network security group](/img/2017-01-02/Ghost/azure-17.png)

8. Cliccare su `Inbound security rules`.

   ![Azure Inbound security rules](/img/2017-01-02/Ghost/azure-18.png)

9. Nell'interfaccia che si apre cliccare su `Add`, configurando la regola con i seguenti parametri e premendo `OK` alla fine della configurazione.

   * Name = default-allow-ghost-test
   * Priority = 1010
   * Source = Any
   * Service = Custom
   * Protocol = TCP
   * Port range = 2368
   * Action = Allow

   ![Azure configurazione parametri regola inbound](/img/2017-01-02/Ghost/azure-19.png)

10. La tabella delle regole inbound dovrebbe presentarsi dopo qualche istante in questo modo.

   ![Azure lista regole inbound](/img/2017-01-02/Ghost/azure-20.png)

A questo punto avevo pensato di aver completato tutto: vado a fare una prova ed ottengo un errore di connessione rifiutata; all'inizio ho pensato che fosse il firewall di Windows a bloccare la comunicazione, ma anche disattivandolo il risultato era lo stesso. 
Ho analizzato con Wireshark ma sinceramente non riuscivo a capire: ho pensato che nella comunicazione venissero passati i pacchetti contrassegnati con l'ip della rete interna su Azure e che quindi questi andasseto persi..ma non era neanche quello il problema.
Per farla breve, cercando su google ho trovato che nel file di configurazione di Ghost, `config.js`, l'ip che viene puntato è sempre quello locale, `127.0.0.1` e quindi qualsiasi richiesta verso un altro indirizzo che non sia quello non viene presa in considerazione; per ovviare a questa situazione basta cambiare nella parte del file indicata come `development` il parametro `host` del `server`, facendolo puntare a `0.0.0.0`.

```javascript
   host: 0.0.0.0,
```

   ![config.js punta a tutti gli indirizzi](/img/2017-01-02/Ghost/Ghost-32.png)

Riavviando Ghost, che di defualt parte in modalità `development`, collegandoci da un browser esterno alla macchina virtuale otteniamo il nostro blog.

Nel prossimo post vi mostrerò invece come caricare Ghost direttamente come sito su Azure, cosa che dovrebbe essere molto più veloce e immediata rispetto a quanto visto.

