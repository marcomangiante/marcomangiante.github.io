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

## Setup di Github Pages

1. Creare un repository del tipo `nomeutente.github.io` con `nomeutente` uguale a quello GitHub.

   <img class="img-responsive" src="/img/GitHub-Pages-Intro/GitHub-Pages-Intro-01.png"/>

2. Una volta creato il repository, scegliere un modo per clonarlo (git, GitHub Desktop, GitHub for Mac).

## Setup del tema da utilizzare

1. Andare al repository GitHub di [Lanyon](https://github.com/poole/lanyon).

2. Cliccare su `Clone or Download` e scaricare il file zip.

3. Estrarre il contenuto del file zip nella direcotry dove avete creato in precedenza il clone del vostro sito.

4. Fare il commit e sync verso il nostro account GitHub.


A questo punto se andate sul link `nomeutente.github.io` dovreste vedere il vostro blog bello e pronto.

## Post

1. Andate nella directory `_posts` e create un file che segua la convenzione `YYYY-mm-dd-titolo-del-post.md`.

2. Inserite all'inizio del file il `layout`, il `titolo` e se volete anche la `data`:

    ---
    layout: post
    title: titolo del post
    date: 2016-12-26
    ---

3. Inserite il testo del post.

Alcuni suggerimenti: per vedere come si formatta un testo in markdown date uno sguardo [qui](https://guides.github.com/features/mastering-markdown/).
Per la scrittura dei post, usate il vostro editor preferito (visto che è un linguaggio semplicemente a marcatori basta anche notepad): io sto utilizzando **Visual Studio Code** che nella stessa interfaccia ha l'editor che supporta `Markdown`(che colora quindi i vari tag utilizzati), la possibilità della preview del file creato e la possibilità di connettersi all'account GitHub per il commit.