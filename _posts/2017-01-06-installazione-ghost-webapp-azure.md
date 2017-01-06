---
layout: post
title: Installazione della piattaforma di blog Ghost su Azure Web Apps 
---
Nel mio ultimo [post](https://marcomangiante.github.io/2017/01/02/installazione-ghost-windows-azure/) ho descritto l'installazione di [Ghost](http://ghost.org) su una macchina virtuale `Windows Server 2016` creata su [Azure](http://portal.azure.com).
In questo post invece voglio illustrare come si può installare più semplicemente Ghost su una `Azure Web Apps`.

In verità ci sono 2 metodi diversi per farlo: li illustro entrambi, anche se sono abbastanza simili.


## Setup via Deploy to Azure

1. Andate sul repository [GitHub](http://github.com/felixrieseberg/Ghost-Azure) di Felix Rieseberg e cliccate su `Deploy to Azure` (se volete potete anche andare su [Ghost-Azure](https://github.com/AzureWebApps/Ghost-Azure), dove c'è la versione Ghost per Azure curata direttamente da Microsoft ma con una release un po' più vecchia).

   ![Ghost-Azure deploy](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-01.png)

2. Nel browser viene caricata una form da compilare

   ![Ghost-Azure form data](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-02.png)

   i cui campi sono

   * Directory
   * Subscription - si sceglie la sottoscrizione alla quale legare la web app e i suoi costi
   * Resource Group - viene richiesto se crearne uno nuovo oppure utilizzare uno creato in precedenza
   * Resource Group Name - il nome da assegnare al Resource Group
   * Site Name - il nome che si vuole dare al sito: la url pubblica con cui sarà raggiungile il blog sarà formata da questo nome + `.azurewebsites.net`
   * Site Location - indica la regione Azure nella quale creare il sito
   * Sku - il tipo di `Pricing tier` da utilizzare; si può scegliere tra
     * Free
     * Shared
     * Basic
     * Standard
     * Premium

3. Una volta cliccato su `Next` nella form, appare una finestra che indica il tipo di risorsa che verrà creato; si clicca quindi su `Deploy`.

   ![Ghost-Azure resource type creation](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-03.png)

4. Inizia il deploy di Ghost su Azure: di solito passano tra i 5 e 10 minuti prima che il tutto sia operativo.

   ![Ghost-Azure inizio deploy](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-04.png)

5. Al termine del deploy

   ![Ghost-Azure inizio deploy](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-05.png)

   si può scegliere di

      i. Andare sulla console di management del sito su Azure.

      ![Ghost creazione account](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-06.png)

      ii. Andare direttamente sul sito creato ed iniziare ad utilizzare la piattaforma.

      ![Ghost credenziali](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-07.png)


## Setup via Azure Marketplace

1. Andare alla pagina [Ghost](http://azure.microsoft.com/en-us/marketplace/partners/ghost/ghost) del Marketplace di Azure e cliccare su `Create Web App`.

   ![Ghost-Azure Marketplace](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-08.png)

2. Una volta inserite le vostre credenziali, si apre il portale di Azure con una form per la creazione della Web App Ghost; i parametri da inserire sono

   * App name - il nome che si vuol dare al sito: la url pubblica con cui sarà raggiungile il blog sarà formata da questo nome + `.azurewebsites.net`
   * Subscription - si sceglie la sottoscrizione alla quale legare la web app e i suoi costi
   * Resource Group - viene richiesto se crearne uno nuovo oppure utilizzare uno creato in precedenza
   * App Service plan/Location - il tipo di `Service Plan` da utilizzare; si può scegliere di

      i. Accettare quello stabilito di default dal sistema

      ![Ghost-Azure Marketplace Service plan default](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-09.png)

      ii. Crearne uno nuovo: click su quello di default, si sceglie `Create New` e si valorizzano i campi terminando con un click su OK

      * App Service Plan - nome che si vuole dare al piano
      * Location - indica la regione Azure nella quale creare il piano
      * Pricing tier - il piano tariffario da utilizzare

      ![Ghost-Azure Marketplace Service plan nuovo](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-10.png)

3. Per iniziare il deploy cliccare su `Create`.

   ![Ghost-Azure Marketplace inizio deploy](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-11.png)

4. Il deploy dura dai 5 ai 10 minuti; viene mostrata la home page del portale di Azure dove si può cliccare sul link alla Web App

   ![Ghost-Azure Marketplace link Web App](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-12.png)

   che porta alla sua console di gestione.

   ![Ghost-Azure Marketplace console gestione Web App](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-13.png)

5. Il processo termina con un pop-up che indica la fine dell'operazione di deploy.

   ![Ghost-Azure Marketplace termine deploy](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-14.png)
   
Qualunque sia stato il metodo utilizzato per il setup di Ghost, bisogna andarlo a configurare.

## Setup di Ghost

1. Aprire una istanza del browser e inserire la url per la gestione del blog:

  * Se si è utilizzato `Deploy to Azure` la url è `Site Name` + `.azurewebsites.net/ghost`.
  * Se si è utilizzato `Azure Marketplace` la url è `App name` + `.azurewebsites.net/ghost`.

   In sequenza

      i. Cliccare su `Create account`

      ![Ghost creazione account](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-15.png)

      ii. Inserire indirizzo mail, nome completo, password per l'accesso all'interfaccia di amministrazione e titolo del blog

      ![Ghost credenziali](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-16.png)

      iii. Inserire persone che partecipino alla gestione del blog (se non si vuole fare in questo momento, cliccare su `I'll do this later, take me to my blog`)

      ![Ghost team](/img/2017-01-06/Ghost-AzureWebApps/ghost-azurewebapps-17.png)

2. Appare l'interfaccia per la gestione del blog e la scrittura dei post.

   ![Ghost gestione e creazione post](/img/2017-01-06/GitHub-Pages-Intro/ghost-azurewebapps-18.png)

Date uno sguardo adesso al blog

   ![Ghost blog](/img/2017-01-06/GitHub-Pages-Intro/ghost-azurewebapps-19.png)


Vi faccio notare che in entrambi i casi la Web App è legata al repository GitHub, quindi se viene aggiornato quest'ultimo basta 

