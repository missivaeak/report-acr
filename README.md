# report-acr

Instruktioner till hur man kan komma igång med ett Azure Container Registry.

## Förutsättningar

Du behöver ha [Azure CLI](https://learn.microsoft.com/en-us/cli/azure/install-azure-cli), [Docker](https://docs.docker.com/get-docker/) och [Docker CLI](https://docs.docker.com/engine/).

Dessutom behöver du ha ett microsoft-konto att logga in på Azure Portal med. Här fungerar ditt studentkonto (kan kräva MFA aktiverat).

## Driftsätta och konfigurera registret

### Skapa resurs
Logga in på [Azure Portal](https://portal.azure.com/). Välj att skapa en ny Container Registry-resurs.

![image1](/img/fig1.png)

---

### Fyll i uppgifter
Fyll i de fält som krävs. Du behöver skapa en ny resursgrupp med länken "create new" samt välja ett namn på Container-registret.

![image1](/img/fig2.png)

---

### Skapa resursen
Klicka på "create". Vänta tills driftsättningen är klar och väl "go to resource".

![image1](/img/fig3.png)

---

### Konfigurera tillgång
Gå till "access control" i navigeringsmenyn på vänster sida.

![image1](/img/fig4.png)

---

### Lägg till ny roll
Klicka på "role assignments" och sen "+ add".

![image1](/img/fig5.png)

---

### Välj rätt roll
Välj rollen "acr push" för rättigheter att pusha och pulla till images i registret.

![image1](/img/fig6.png)

---

### Lägg till personer i rollen
Tryck på länken "+ select members".

![image1](/img/fig7.png)

---

### Sök efter personer
Sök efter de personer som du vill lägg till i den valda rollen. `acr push` i detta exempel.

![image1](/img/fig8.png)

---

### Notera login server
Gå tillbaka till resursens överblick och notera "login server". `testtechreport.azurecr.io` i detta exemplet.

![image1](/img/fig9.png)

## Ansluta DockerCLI till ACR
För att kunna börja använda ditt ACR behöver du logga in och ansluta det till docker.

Logga in på AzureCLI:
```
az login
```

Anslut ditt ACR (ersätt testtechreport med ditt registers namn):
```
az acr login --name testtechreport
```

> [!NOTE]
> Du kan behöva köra detta kommando varje gång du startar om ditt system.

Nu bör du vara redo att börja använda ditt ACR.

Testa genom att köra dessa kommandon. Först hämtar du en test-image.
```
docker pull mcr.microsoft.com/mcr/hello-world
```

Sen kan du tagga den att tillhöra ditt ACR och pusha den. Använd din "login server" som du noterade när du skapade resursen.
```
docker tag mcr.microsoft.com/mcr/hello-world testtechreport.azurecr.io/samples/hello-world
docker push testtechreport.azurecr.io/samples/hello-world
```

Nu är den imagen i ditt ACR. Du kan hämta den med detta kommando:
```
docker pull testtechreport.azurecr.io/samples/hello-world
```

__Enjoy!__
