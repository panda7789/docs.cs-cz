---
title: Sestavování aplikací ASP.NET Core 2,2 nasazených jako kontejnery Linux do clusterů AKS/Kubernetes
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: 89843e0041c12f001f974360da2e5903499155d1
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295353"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Sestavování aplikací ASP.NET Core 2,2 nasazených jako kontejnery Linux do AKS/Kubernetes Orchestrator

Azure Kubernetes Services (AKS) jsou spravované služby Kubernetes orchestrace v Azure, které zjednodušují nasazení a správu kontejnerů.

AKS hlavní funkce:

- Rovina řízení hostovaná v Azure
- Automatizované upgrady
- Samo – opravit
- Uživatelsky konfigurovatelné škálování
- Jednodušší uživatelské prostředí pro vývojáře i pro operátory clusterů.

Následující příklady Prozkoumejte vytvoření aplikace ASP.NET Core 2,2, která běží na platformě Linux a nasadí do clusteru AKS v Azure, zatímco vývoj se provádí pomocí sady Visual Studio 2017.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Vytvoření projektu ASP.NET Core 2,2 pomocí sady Visual Studio 2017

ASP.NET Core je vývojová platforma pro obecné účely udržovaná Microsoftem a komunitou .NET na GitHubu. Je to podpora pro různé platformy, Windows, macOS a Linux a dá se použít v scénářích zařízení, Cloud a integrovaných a IoT.

V tomto příkladu se používá jednoduchý projekt založený na šabloně webového rozhraní API sady Visual Studio, takže k vytvoření ukázky nepotřebujete žádné další znalosti. Projekt je nutné vytvořit pouze pomocí standardní šablony, která obsahuje všechny prvky pro spuštění malého projektu s REST API pomocí technologie ASP.NET Core 2,2.

![Přidejte nové okno projektu v aplikaci Visual Studio a vyberte ASP.NET Core webové aplikace.](media/create-aspnet-core-application.png)

**Obrázek 4-36**. Vytváření ASP.NET Core aplikace

Chcete-li vytvořit ukázkový projekt v aplikaci Visual Studio, vyberte **soubor** > **Nový** > **projekt**, v levém podokně vyberte typy **webových** projektů a potom **ASP.NET Core webové aplikace**.

Visual Studio obsahuje šablony pro webové projekty. V našem příkladu vyberte **rozhraní API** a vytvořte aplikaci webového rozhraní api pro ASP.NET.

Ověřte, že jste vybrali ASP.NET Core 2,2 jako rozhraní. .NET Core 2,2 je součástí poslední verze sady Visual Studio 2017 a při instalaci sady Visual Studio 2017 se automaticky nainstaluje a nakonfiguruje.

![Dialog sady Visual Studio pro výběr typu ASP.NET Core webové aplikace s vybranou možností rozhraní API.](media/create-web-api-application.png)

**Obrázek 4-37**. Výběr typu projektu ASP.NET CORE 2,2 a webového rozhraní API

Pokud máte předchozí verzi rozhraní .NET Core, můžete si stáhnout a nainstalovat verzi 2,2 z <https://www.microsoft.com/net/download/core#/sdk>.

Můžete přidat podporu Docker při vytváření projektu nebo následně, abyste mohli projekt kdykoli "ukotvovat". Chcete-li přidat podporu Docker po vytvoření projektu, klikněte pravým tlačítkem myši na uzel projektu v Průzkumník řešení a v místní nabídce vyberte **Přidat** > **podporu Docker** .

![Možnost místní nabídky pro přidání podpory Docker do existujícího projektu: Klikněte pravým tlačítkem (na projekt) > přidat podporu pro > Docker.](media/add-docker-support-to-project.png)

**Obrázek 4-38**. Přidání podpory Docker do existujícího projektu

Pokud chcete dokončit přidávání podpory Docker, můžete zvolit Windows nebo Linux. V takovém případě vyberte **Linux**, protože AKS nepodporuje kontejnery Windows (od nejnovějšího 2018).

![Dialog možností pro výběr cílového OS pro souboru Dockerfile.](media/select-linux-docker-support.png)

**Obrázek 4-39**. Výběr kontejnerů Linux.

V těchto jednoduchých krocích máte aplikaci ASP.NET Core 2,2 běžící v kontejneru Linux.

Jak vidíte, integrace mezi Visual Studio 2017 a Docker je zcela zaměřená na produktivitu vývojářů.

Nyní můžete spustit aplikaci pomocí klávesy **F5** nebo pomocí tlačítka **Přehrát** .

Po spuštění projektu můžete zobrazit seznam imagí pomocí `docker images` příkazu. Měli byste vidět `mssampleapplication` image vytvořenou automatickým nasazením našeho projektu pomocí sady Visual Studio 2017.

```console
docker images
```

![Výstup konzoly z příkazu Docker images zobrazuje seznam s: Úložiště, značka, ID obrázku, Vytvořeno (datum) a velikost.](media/docker-images-command.png)

**Obrázek 4-40**. Zobrazení imagí Docker

## <a name="register-the-solution-in-the-azure-container-registry"></a>Zaregistrujte řešení v Azure Container Registry

Nahrajte image do libovolného registru Docker, jako je [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) nebo Docker Hub, aby bylo možné image nasadit do clusteru AKS z tohoto registru. V tomto případě nahrajeme obrázek do Azure Container Registry.

### <a name="create-the-image-in-release-mode"></a>Vytvoření image v režimu vydání

Nyní vytvoříme bitovou kopii v režimu **vydání** (připraveno pro produkční prostředí) tak, že se změní na **release**, jak je znázorněno na obrázku 4-41 a aplikace se spustí stejně jako dřív.

![Možnost panelu nástrojů v sadě VS k sestavení v režimu vydání.](media/select-release-mode.png)

**Obrázek 4-41**. Výběr režimu vydání

Pokud příkaz provedete, zobrazí se oba vytvořené bitové kopie, jeden pro `debug` a druhý pro `release` režim. `docker image`

### <a name="create-a-new-tag-for-the-image"></a>Vytvořit novou značku pro obrázek

Každá image kontejneru musí být označena `loginServer` názvem registru. Tato značka se používá pro směrování při vkládání imagí kontejneru do registru imagí.

`loginServer` Název můžete zobrazit z Azure Portal a přebírat informace z Azure Container Registry

![V prohlížeči se zobrazí název služby Azure Container Registry v pravém horním rohu.](media/loginServer-name.png)

**Obrázek 4-42**. Zobrazení názvu registru

Nebo spuštěním následujícího příkazu:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup konzoly z výše uvedeného příkazu](media/az-cli-loginServer-name.png)

**Obrázek 4-43**. Získání názvu registru pomocí PowerShellu

V obou případech získáte název. V našem příkladu `mssampleacr.azurecr.io`.

Nyní můžete označit Image pomocí nejnovější bitové kopie (obrázek verze) a příkazu:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Po spuštění `docker tag` příkazu vypište obrázky `docker images` pomocí příkazu a měli byste vidět obrázek s novou značkou.

![Výstup konzoly z příkazu Docker images](media/tagged-docker-images-list.png)

**Obrázek 4-44**. Zobrazení tagovaných obrázků

### <a name="push-the-image-into-the-azure-acr"></a>Vložení image do Azure ACR

Přihlášení k Azure Container Registry

```console
az acr login --name mssampleacr
```

Nahrajte image do Azure ACR pomocí následujícího příkazu:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Tento příkaz při nahrávání imagí trvá, ale v procesu vám poskytne zpětnou vazbu.

![Výstup konzoly z příkazu Docker push: zobrazuje indikátor průběhu na základě znaků pro každou vrstvu.](media/uploading-image-to-acr.png)

**Obrázek 4-45**. Obrázek se nahrává do ACR.

Vidíte pod výsledek, který byste měli získat po dokončení procesu:

![Výstup konzoly z příkazu Docker push, dokončený, zobrazení všech vrstev nebo uzlů](media/uploading-docker-images-complete.png)

**Obrázek 4-46**. Zobrazení uzlů

Dalším krokem je nasazení kontejneru do clusteru AKS Kubernetes. V takovém případě potřebujete soubor (**soubor. yml Deploy**), který obsahuje následující:

```yml
apiVersion: apps/v1beta1
kind: Deployment
metadata:
  name: mssamplesbook
spec:
  replicas: 1
  template:
    metadata:
      labels:
        app: mssample-kub-app
    spec:
      containers:
        - name: mssample-services-app
          image: mssampleacr.azurecr.io/mssampleaksapplication:v1
          ports:
            - containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
    name: mssample-kub-app
spec:
  ports:
    - name: http-port
      port: 80
      targetPort: 80
  selector:
    app: mssample-kub-app
  type: LoadBalancer
```

> [!NOTE]
> Další informace o nasazení pomocí Kubernetes najdete v tématech:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Teď jste skoro připraveni nasadit pomocí **Kubectl**, ale nejdřív musíte získat přihlašovací údaje do clusteru AKS pomocí tohoto příkazu:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Výstup z konzoly z výše uvedeného příkazu: Sloučí se MSSampleK8Cluster jako aktuální kontext v/root/.Kube/config.](media/getting-aks-credentials.png)

**Obrázek 4-47**. získávání přihlašovacích údajů

Pak pomocí `kubectl create` příkazu spusťte nasazení.

```console
kubectl create -f mssample-deploy.yml
```

![Výstup z konzoly z výše uvedeného příkazu: bylo vytvořeno nasazení mssamplesbook. Služba "mssample-Kub-App" byla vytvořena.](media/kubectl-create-command.png)

**Obrázek 4-48**. Nasazení na Kubernetes

Až se nasazení dokončí, můžete ke konzole Kubernetes přistupovat pomocí místního proxy serveru, ke kterému se můžete dostat do dočasného přístupu pomocí tohoto příkazu:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

A přistupuje k adrese `http://127.0.0.1:8001`URL.

![Zobrazení prohlížeče řídicího panelu Kubernetes zobrazující nasazení, lusky, sady replik a služby.](media/kubernetes-cluster-information.png)

**Obrázek 4-49**. Zobrazit informace o clusteru Kubernetes

Nyní máte aplikaci nasazenou v Azure, pomocí kontejneru Linux a clusteru AKS Kubernetes. Přístup k vaší aplikaci můžete zpřístupnit do veřejné IP adresy vaší služby, kterou můžete získat z Azure Portal.

> [!NOTE]
> V této příručce najdete informace o tom, jak vytvořit cluster AKS pro tuto ukázku v oddílu [**nasazení do služby Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) .

>[!div class="step-by-step"]
>[Předchozí](set-up-windows-containers-with-powershell.md)Další
>[](../docker-devops-workflow/index.md)
