---
layout: post
title: Introduzione a GitHub Pages come piattaforma per il blogging
---
Sono arrivato a [GitHub Pages](https://pages.github.com/) per caso, guardando il blog di [Scott Lowe](https://blog.scottlowe.org) e chiedendogli via twitter su quale piattaforma fosse stato implementato.

Non pensavo che GitHub permettesse di avere, in modo del tutto gratuito, un blog ospitato sui loro server sfruttando in pratica la loro tecnologia; inutile mettermi a spiegare come funzioni il tutto quando basta dare una letta [qui](https://jekyllrb.com/docs/github-pages/).

Fare il setup iniziale di GitHub Pages non è stato difficile, anzi; un po' più complicato è stato creare qualcosa di simile al blog di Scott almeno come veste grafica applicando lo stesso tema da lui utilizzato, [Lanyon](http://lanyon.getpoole.com/).

Non essendo super pratico di GitHub, ci ho messo un po' a capire i meccanismi disponibili e qualche giorno è corso via perché non riuscivo a capire quale fosse un problema di rendering che si creava nella barra laterale del menù del blog, salvo poi accorgermi di un problema relativo ai permalink e in particolare ad una linea presente nel file `_config.yml` che doveva essere commentata e che invece nell'originale del tema Lanyon non lo era.

Questo post (che tra l'altro è il primo che faccio su questa nuova piattaforma) serve ad aiutare chi, come me, ha avuto o ha difficoltà nel setup di un sito per il primo post con GitHub Pages..o semplicemente può servire a chi può maturare un interesse in questa tecnologia e vuole saperne di più.

Quello che mi propongo è quello di far in modo che in pochi minuti siate in grado di scrivere un post sul vostro blog "powered by GitHub Pages".

## Setup di GitHub Desktop

1. Andare alla pagina [GitHub Desktop](http://desktop.github.com) e cliccare su `Download`

   ![Download GitHub Desktop](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-01.png)

2. Dopo qualche secondo apparirà la dialog per l'installazione del software

   ![Installa GitHub Desktop](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-02.png)

3. Il file da scaricare è di 127 MB, ci vorrà qualche attimo per scaricarlo

   ![Progess GitHub Desktop](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-03.png)

4. Terminato il download, si apre l'interfaccia per configurare il client 

      i. Per prima cosa, bisogna inserire user e password di GitHub e quindi cliccare su `Log in`

      ![GitHub Desktop Login](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-04.png)

      ii. Si passa quindi alla configurazione di Git, dove vengono inseriti username e l'indirizzo mail che vorremo utilizzare per i commit

      ![GitHub Git Login](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-05.png)

      iii. Non avendo un repository da sincronizzare, cliccare su `Skip`

      ![GitHub Repository Skip](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-06.png)
 
## Setup di Github Pages e configurazione in locale

1. Andare sul proprio account `GitHub` e cliccare su `New repository`.

   ![GitHub creazione repository](img/GitHub-Pages-Intro/GitHub-Pages-Intro-01.png)

2. Creare un repository del tipo `nomeutente.github.io` con `nomeutente` uguale a quello GitHub.

   ![GitHub Pages configurazione repository](img/GitHub-Pages-Intro/GitHub-Pages-Intro-02.png)

3. Una volta creato il repository, cliccare su `Set up in Desktop`.

   ![GitHub repository nel Desktop](img/GitHub-Pages-Intro/GitHub-Pages-Intro-03.png)

4. Dopo aver dato l'assenso all'apertura di GitHub Desktop, il programma si apre mostrando una dialog nella quale scegliere quale sarà il percorso locale del repository: di solito viene suggerita una cartella `GitHub` sotto `Documenti`.

   ![GitHub Desktop repository locale](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-07.png)

5. A questo punto, l'intera struttura del repository su `GitHub` viene clonata in locale nella directory precedentemente individuata.

   ![GitHub clone repository](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-08.png)

6. Alla fine del processo di clone, in alto a sinistra si avrà a disposizione il link al repository.

   ![GitHub link repository locale](img/GitHub-Desktop-Installation/GitHub-Desktop-Installation-09.png)  

## Setup del tema da utilizzare

1. Andare sul repository GitHub di [Lanyon](https://github.com/poole/lanyon), cliccare su `Clone or Download` e quindi su `Scarica il file zip`. 

   ![GitHub download Lanyon](img/GitHub-Pages-Intro/GitHub-Theme-01.png)

2. Aprire il file zip e quindi entrare nella direcotory `lanyon-master` e copiare l'intero contenuto.

   ![GitHub copiare tema](img/GitHub-Pages-Intro/GitHub-Theme-02.png)

3. Incollare i file e directory copiati, nel passo precedente, nella directory creata per il repository locale.

   ![GitHub incollare tema](img/GitHub-Pages-Intro/GitHub-Theme-03.png)

4. Andare a modificare il file `_config.yml` (basta un semplice editor di testo), commentando con un `#` la linea:

   ```Markdown
   relative_permalinks: true
   ```

5. Aprire `GitHub Desktop`, selezionare il repository creato, fare il commit aggiungendo un riepilogo e una breve descrizione.

   ![GitHub commit](img/GitHub-Pages-Intro/GitHub-Commit.png)

6. Fare il `Publish` verso `GitHub`.

   ![GitHub sync](img/GitHub-Pages-Intro/GitHub-Publish.png)


Se a questo punto andate su `https://nomeutente.github.io` dovreste vedere la struttura del vostro blog bella e pronta

![GitHub Sito](img/GitHub-Pages-Intro/GitHub-Sito-01.png)

Se non doveste vedere alcun risultato, oppure ottenere un errore 404, andate sul vostro repository `https://github.com/nomeutente/nomeutente.github.io/settings` (per vedere la 
pagina dovete aver fatto il login in precedenza) e verificate che nella parte `GitHub Pages` ci sia una spunta verde con vicino il commento `Your site is published at...`.

![GitHub Settings](img/GitHub-Pages-Intro/GitHub-Sito-02.png)

La struttura è pronta, ma senza `post` che blog è?  

## Creazione del primo Post

1. Andate nel repository che avete localmente, nella directory `_posts` e create un file che segua la convenzione `YYYY-mm-dd-titolo-del-post.md`.

   ![GitHub creazione file post](img/GitHub-Pages-Intro/GitHub-Post-01.png)

2. Inserite all'inizio del file i marcatori `layout` e `titolo` (con valori simili a quelli nell'esempio):

```Markdown
    ---
    layout: post
    title: titolo del post
    ---
```

3. Inserite il testo del post.

Alcuni suggerimenti per la scrittura dei post:

* per vedere come si formatta un testo in markdown, date uno sguardo [qui](https://guides.github.com/features/mastering-markdown/)
* guardate i post di esempio, nel caso modificate direttamente quelli (io ho iniziato così per capire come funzionassero i marcatori)
* usate il vostro editor preferito (basta anche notepad): io sto utilizzando **Visual Studio Code** che nella stessa interfaccia ha l'editor che supporta `Markdown`(che colora quindi i vari tag utilizzati), la possibilità della preview del file creato e la possibilità di connettersi all'account GitHub per il commit.