# report-acr

Instruktioner till hur man kan komma igång med ett Azure Container Registry.

## Förutsättningar

Du behöver ha [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli), [Docker](https://docs.docker.com/get-docker/) och [Docker CLI](https://docs.docker.com/engine/).

Dessutom behöver du ha ett microsoft-konto att logga in på Azure Portal med. Här fungerar ditt studentkonto (kan kräva MFA aktiverat).

## Driftsätta och konfigurera registret

### Skapa resurs

Logga in på [Azure Portal](https://portal.azure.com/). Välj att skapa en ny Container Registry-resurs.

> ![image1](/img/fig1.png)

---

### Fyll i uppgifter

Fyll i de fält som krävs. Du behöver skapa en ny resursgrupp med länken "create new" samt välja ett namn på Container-registret.

> ![image1](/img/fig2.png)

### Skapa resursen

Klicka på "create". Vänta tills driftsättningen är klar och väl "go to resource".

> ![image1](/img/fig3.png)

### Konfigurera tillgång

Gå till "access control" i navigeringsmenyn på vänster sida.

> ![image1](/img/fig4.png)

### Lägg till ny roll

Klicka på "role assignments" och sen "+ add".

> ![image1](/img/fig5.png)

### Välj rätt roll

Välj rollen "acr push" för rättigheter att pusha och pulla till images i registret.

> ![image1](/img/fig6.png)

### Lägg till personer i rollen

Tryck på länken "+ select members".

> ![image1](/img/fig7.png)

### Sök efter personer

Sök efter de personer som du vill lägg till i den valda rollen. `acr push` i detta exempel.

> ![image1](/img/fig8.png)

### Notera login server

Gå tillbaka till resursens överblick och notera "login server". `testtechreport.azurecr.io` i detta exemplet.

> ![image1](/img/fig9.png)

##
