---
title: Sestavování aplikací ASP.NET Core nasazených jako kontejnery Linux do clusterů AKS/Kubernetes
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 08/06/2020
ms.openlocfilehash: 4b04e5d56c73918c665ad6e2825205870aac9606
ms.sourcegitcommit: ef50c99928183a0bba75e07b9f22895cd4c480f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/07/2020
ms.locfileid: "87916453"
---
# <a name="build-aspnet-core-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Sestavování aplikací ASP.NET Core nasazených jako kontejnery Linux do nástroje AKS/Kubernetes Orchestrator

Azure Kubernetes Services (AKS) jsou spravované služby Kubernetes orchestrace v Azure, které zjednodušují nasazení a správu kontejnerů.

AKS hlavní funkce:

- Rovina řízení hostovaná v Azure
- Automatizované upgrady
- Samoopravování
- Uživatelsky konfigurovatelné škálování
- Jednodušší uživatelské prostředí pro vývojáře i pro operátory clusterů.

Následující příklady Prozkoumejte vytvoření aplikace ASP.NET Core 3,1, která běží na platformě Linux a nasadí do clusteru AKS v Azure, zatímco vývoj se provádí pomocí sady Visual Studio 2019.

## <a name="creating-the-aspnet-core-project-using-visual-studio-2019"></a>Vytvoření projektu ASP.NET Core pomocí sady Visual Studio 2019

ASP.NET Core je vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na GitHubu. Je to podpora pro různé platformy, Windows, macOS a Linux a dá se použít v scénářích zařízení, Cloud a integrovaných a IoT.

V tomto příkladu se používá několik jednoduchých projektů založených na šablonách sady Visual Studio, takže nepotřebujete mít spoustu dalších znalostí pro vytvoření ukázky. Projekt je třeba vytvořit pomocí standardní šablony, která obsahuje všechny prvky pro spuštění malého projektu s REST API a webovou aplikací se stránkami Razor pomocí technologie ASP.NET Core 3,1.

![Přidejte nové okno projektu v aplikaci Visual Studio a vyberte ASP.NET Core webové aplikace.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-aspnet-core-application.png)

**Obrázek 4-35**. Vytvoření webové aplikace v ASP.NET Core v aplikaci Visual Studio 2019.

Chcete-li vytvořit ukázkový projekt v aplikaci Visual Studio, vyberte **soubor**  >  **Nový**  >  **projekt**, vyberte typ **webového** projektu a poté šablonu **ASP.NET Core webové aplikace** . Šablonu můžete vyhledat také v případě, že ji potřebujete.

Pak zadejte název a umístění aplikace, jak je znázorněno na následujícím obrázku.

![Zadejte název projektu a jeho umístění.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/enter-project-name-and-location.png)

**Obrázek 4-36**. Zadejte název projektu a umístění v aplikaci Visual Studio 2019.

Ověřte, že jste vybrali ASP.NET Core 3,1 jako rozhraní. Rozhraní .NET Core 3,1 je součástí nejnovější verze sady Visual Studio 2019 a při instalaci sady Visual Studio je automaticky nainstalováno a nakonfigurováno.

![Dialog sady Visual Studio pro výběr typu ASP.NET Core webové aplikace s vybranou možností rozhraní API.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/create-web-api-application.png)

**Obrázek 4-37**. Výběr typu projektu ASP.NET CORE 3,1 a webového rozhraní API

Podpora Docker není teď zapnutá, takže ji můžete zobrazit až po vytvoření projektu.

Pokud máte předchozí verzi rozhraní .NET Core, můžete si stáhnout a nainstalovat verzi 3,1 z <https://dotnet.microsoft.com/download> .

Pokud se chcete podívat, jak se váš projekt stane ukotvovat, můžete teď přidat podporu Docker. V Průzkumník řešení klikněte pravým tlačítkem myši na uzel projektu a v místní nabídce vyberte **Přidat**  >  **podporu Docker** .

![Možnost místní nabídky pro přidání podpory Docker do existujícího projektu: klikněte pravým tlačítkem (v projektu) > přidat podporu > Docker.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-docker-support-to-project.png)

**Obrázek 4-38**. Přidání podpory Docker do existujícího projektu

Pokud chcete dokončit přidávání podpory Docker, můžete zvolit Windows nebo Linux. V takovém případě vyberte **Linux**.

![Dialog možností pro výběr cílového OS pro souboru Dockerfile.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-linux-docker-support.png)

**Obrázek 4-39**. Výběr kontejnerů Linux.

V těchto jednoduchých krocích máte aplikaci ASP.NET Core 3,1 běžící v kontejneru Linux.

Podobným způsobem můžete také přidat velmi jednoduchý projekt **WebApp** (obrázek 4-40) pro využívání koncového bodu webového rozhraní API, i když zde podrobnosti nejsou popsané.

Potom přidáte podporu nástroje Orchestrator pro projekt **WebApi** , jak je uvedeno dále, v imagi 4-40.

![Přidání podpory nástroje Orchestrator do projektu WebApi](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/add-orchestrator-support.png)

**Obrázek 4-40**. Do projektu *WebApi* se přidává podpora nástroje Orchestrator.

Když zvolíte `Docker Compose` možnost, která je pro místní vývoj vhodná, Visual Studio přidá do souboru Docker-Docker projekt, jak je znázorněno na obrázku 4-41.

![Docker – sestavení přidané do řešení](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-compose-project-in-visual-studio.png)

**Obrázek 4-41**. Do projektu *WebApi* se přidává podpora nástroje Orchestrator.

Počáteční přidané soubory jsou podobné těm:

`docker-compose.yml`

```yml
version: "3.4"

services:
  webapi:
    image: ${DOCKER_REGISTRY-}webapi
    build:
      context: .
      dockerfile: WebApi/Dockerfile

  webapp:
    image: ${DOCKER_REGISTRY-}webapp
    build:
      context: .
      dockerfile: WebApp/Dockerfile
```

`docker-compose.override.yml`

```yml
version: "3.4"

services:
  webapi:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
  webapp:
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
      - ASPNETCORE_URLS=https://+:443;http://+:80
    ports:
      - "80"
      - "443"
    volumes:
      - ${APPDATA}/Microsoft/UserSecrets:/root/.microsoft/usersecrets:ro
      - ${APPDATA}/ASP.NET/Https:/root/.aspnet/https:ro
```

Pokud chcete, aby aplikace běžela s Docker Compose stačí provést několik vylepšení`docker-compose.override.yml`

```yml
services:
  webapi:
    #...
    ports:
      - "51080:80"
      - "51443:443"
    #...
  webapp:
    environment:
      #...
      - WebApiBaseAddress=http://webapi
    ports:
      - "50080:80"
      - "50443:443"
    #...
```

Nyní můžete spustit aplikaci pomocí klávesy **F5** nebo pomocí tlačítka **Přehrát** nebo **stisknutím klávesy CTRL + F5** vybrat projekt Docker – sestavení, jak je znázorněno na obrázku 4-42.

![Spuštění aplikace Docker – sestavení projektu se sadou Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/running-docker-compose-with-visual-studio.png)

**Obrázek 4-42**. Do projektu *WebApi* se přidává podpora nástroje Orchestrator.

Při spuštění aplikace Docker-tváře, která je vysvětlena, získáte:

1. Obrázky sestavené a kontejnery vytvořené podle souboru Docker – pro sestavení.
2. Prohlížeč je otevřen v adrese konfigurované v dialogovém okně vlastnosti `docker-compose` projektu.
3. Okno **kontejneru** otevřené (v aplikaci Visual Studio 2019 verze 16,4 a novější).
4. Podpora ladicího programu pro všechny projekty v řešení, jak je znázorněno na následujících obrázcích.

Otevřený prohlížeč:

![Zobrazení prohlížeče s webovou aplikací spuštěnou](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/browser-opened.png)

**Obrázek 4-43**. Okno prohlížeče s aplikací spuštěnou na více kontejnerech.

Okno kontejnery:

![Okno kontejnerů sady Visual Studio](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/visual-studio-containers-window.png)

**Obrázek 4-44**. Okno kontejnerů sady Visual Studio

Okno **kontejnery** umožňuje zobrazit spuštěné kontejnery, procházet dostupné image, zobrazovat proměnné prostředí, protokoly a mapování portů, kontrolovat systém souborů, připojit ladicí program nebo otevřít okno terminálu v prostředí kontejneru.

Jak vidíte, integrace mezi Visual Studio 2019 a Docker je zcela zaměřená na produktivitu vývojářů.

Pomocí příkazu je samozřejmě můžete také zobrazit seznam imagí `docker images` . Měli byste vidět `webapi` image a `webapp` s `dev` značkami vytvořenými automatickým nasazením našeho projektu pomocí sady Visual Studio 2019.

```console
docker images
```

![Výstup konzoly z příkazu Docker images zobrazuje seznam s: úložiště, značka, ID obrázku, Vytvořeno (datum) a velikost.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/docker-images-command.png)

**Obrázek 4-45**. Zobrazení imagí Docker

## <a name="register-the-solution-in-an-azure-container-registry-acr"></a>Registrace řešení v Azure Container Registry (ACR)

Obrázky můžete nahrát do [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/), ale můžete také použít Docker Hub nebo jakýkoli jiný registr, aby bylo možné image nasadit do clusteru AKS z tohoto registru.

### <a name="create-an-acr-instance"></a>Vytvoření instance ACR

Z příkazu **AZ CLI**spusťte následující příkaz:

```powershell
az acr create --name exploredocker --resource-group explore-docker-aks-rg --sku basic --admin-enabled
```

### <a name="create-the-image-in-release-mode"></a>Vytvoření image v režimu vydání

Bitovou kopii teď vytvoříte v režimu **vydání** (připravené pro produkční prostředí) tak, že změníte **verzi**, jak je znázorněno na obrázku 4-46, a spustíte aplikaci stejným způsobem jako předtím.

![Možnost panelu nástrojů v sadě VS k sestavení v režimu vydání.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/select-release-mode.png)

**Obrázek 4-46**. Výběr režimu vydání

Pokud `docker images` příkaz spustíte, zobrazí se oba vytvořené bitové kopie, jeden pro `debug` (**vývoj**) a druhý pro `release` (**nejnovější**) režim.

### <a name="create-a-new-tag-for-the-image"></a>Vytvořit novou značku pro obrázek

Každá image kontejneru musí být označena `loginServer` názvem registru. Tato značka se používá pro směrování při nahrávání imagí kontejneru do registru imagí.

Název můžete zobrazit `loginServer` z Azure Portal a přebírat informace z Azure Container Registry

![V prohlížeči se zobrazí název služby Azure Container Registry v pravém horním rohu.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/loginServer-name.png)

**Obrázek 4-47**. Zobrazení názvu registru

Nebo spuštěním následujícího příkazu:

```console
az acr list --resource-group <resource-group-name> --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup konzoly z výše uvedeného příkazu](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/az-cli-loginServer-name.png)

**Obrázek 4-48**. Získání názvu registru pomocí **AZ CLI**

V obou případech získáte název. V našem příkladu `exploredocker.azurecr.io` .

Nyní můžete označit Image pomocí nejnovější bitové kopie (obrázek verze) a příkazu:

```console
docker tag <image-name>:latest <login-server-name>/<image-name>:v1
```

Po spuštění příkazu vypište `docker tag` obrázky pomocí `docker images` příkazu a měli byste vidět obrázek s novou značkou.

![Výstup konzoly z příkazu Docker images](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/tagged-docker-images-list.png)

**Obrázek 4-49**. Zobrazení tagovaných obrázků

### <a name="push-the-image-into-the-azure-acr"></a>Vložení image do Azure ACR

Přihlášení k Azure Container Registry

```console
az acr login --name exploredocker
```

Nahrajte image do Azure ACR pomocí následujícího příkazu:

```console
docker push <login-server-name>/<image-name>:v1
```

Tento příkaz při nahrávání imagí trvá, ale v procesu vám poskytne zpětnou vazbu. Na následujícím obrázku vidíte výstup z jedné image dokončeno a další probíhá.

![Výstup konzoly z příkazu Docker push](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/uploading-docker-images-complete.png)

**Obrázek 4-50**. Výstup konzoly z příkazu push

K nasazení aplikace pro více kontejnerů do clusteru AKS potřebujete některé `.yaml` soubory manifestu, které mají většinu vlastností ze `docker-compose.yml` `docker-compose.override.yml` souborů a.

#### `deploy-webapi.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapi
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapi
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapi
    spec:
      containers:
        - name: webapi
          image: exploredocker.azurecr.io/webapi:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
---
apiVersion: v1
kind: Service
metadata:
  name: webapi
  labels:
    app: weather-forecast
    service: webapi
spec:
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapi
```

#### `deploy-webapp.yml`

```yml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp
  labels:
    app: weather-forecast
spec:
  replicas: 1
  selector:
    matchLabels:
      service: webapp
  template:
    metadata:
      labels:
        app: weather-forecast
        service: webapp
    spec:
      containers:
        - name: webapp
          image: exploredocker.azurecr.io/webapp:v1
          imagePullPolicy: IfNotPresent
          ports:
            - containerPort: 80
              protocol: TCP
          env:
            - name: ASPNETCORE_URLS
              value: http://+:80
            - name: WebApiBaseAddress
              value: http://webapi
---
apiVersion: v1
kind: Service
metadata:
  name: webapp
  labels:
    app: weather-forecast
    service: webapp
spec:
  type: LoadBalancer
  ports:
    - port: 80
      targetPort: 80
      protocol: TCP
  selector:
    service: webapp
```

> [!NOTE]
> Předchozí `.yml` soubory povolují pouze `HTTP` porty pomocí `ASPNETCORE_URLS` parametru, aby nedocházelo k problémům s chybějícím certifikátem v ukázkové aplikaci.

> [!TIP]
> V této příručce najdete informace o tom, jak vytvořit cluster AKS pro tuto ukázku v oddílu [**nasazení do služby Azure Kubernetes Service (AKS)**](deploy-azure-kubernetes-service.md) .

Teď jste skoro připraveni nasadit pomocí **kubectl**, ale nejdřív musíte získat přihlašovací údaje z clusteru AKS pomocí tohoto příkazu:

```console
az aks get-credentials --resource-group explore-docker-aks-rg --name explore-docker-aks
```

![Výstup z konzoly z výše uvedeného příkazu: "prozkoumává-Docker-AKS" jako aktuální kontext v C:\Users\Miguel.kube\config](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/getting-aks-credentials.png)

**Obrázek 4-51**. Získávání přihlašovacích údajů z AKS do prostředí kubectl

Musíte taky dovolit, aby cluster AKS vyčetl image z ACR pomocí tohoto příkazu:

```console
az aks update --name explore-docker-aks --resource-group explore-docker-aks-rg --attach-acr exploredocker
```

Dokončení předchozího příkazu může trvat několik minut. Pak pomocí `kubectl apply` příkazu spusťte nasazení a pak `kubectl get all` Získejte seznam objektů clusteru.

```console
kubectl apply -f deploy-webapi.yml
kubectl apply -f deploy-webapp.yml

kubectl get all
```

![Výstup z konzoly z výše uvedených příkazů: nasazení byla aplikována. služby se vytvořily.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubectl-apply-command.png)

**Obrázek 4-52**. Nasazení do Kubernetes

Budete muset chvíli počkat, dokud nástroj pro vyrovnávání zatížení nezíská externí IP adresu, zkontroluje se `kubectl get services` a pak by aplikace měla být k dispozici na adrese, jak je znázorněno na následujícím obrázku:

![Zobrazení prohlížeče aplikace nasazené do AKS](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/aks-deployed-application.png)

**Obrázek 4-53**. Nasazení do Kubernetes

Po dokončení nasazení můžete k [webovému uživatelskému rozhraní Kubernetes](https://kubernetes.io/docs/tasks/access-application-cluster/web-ui-dashboard/) přistupovat pomocí místního proxy serveru pomocí tunelu SSH.

Nejprve musíte vytvořit ClusterRoleBinding pomocí následujícího příkazu:

```console
kubectl create clusterrolebinding kubernetes-dashboard --clusterrole=cluster-admin --serviceaccount=kube-system:kubernetes-dashboard
```

A potom tento příkaz spustí proxy:

```console
az aks browse --resource-group exploredocker-aks-rg --name explore-docker-aks
```

Mělo by se otevřít okno prohlížeče `http://127.0.0.1:8001` s podobným zobrazením:

![Zobrazení prohlížeče řídicího panelu Kubernetes zobrazující nasazení, lusky, sady replik a služby.](media/build-aspnet-core-applications-linux-containers-aks-kubernetes/kubernetes-cluster-information.png)

**Obrázek 4-54**. Zobrazit informace o clusteru Kubernetes

Nyní máte aplikaci ASP.NET Core, která běží v kontejnerech Linux a nasazená do clusteru AKS v Azure.

> [!NOTE]
> Další informace o nasazení pomocí Kubernetes najdete v tématech:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

> [!div class="step-by-step"]
> [Předchozí](set-up-windows-containers-with-powershell.md) 
>  [Další](../docker-devops-workflow/index.md)
