---
title: Vytváření aplikací ASP.NET Core 2.2 nasazených jako linuxové kontejnery do clusterů AKS/Kubernetes
description: Životní cyklus kontejnerizované aplikace Dockeru s platformou a nástroji Microsoft
ms.date: 02/25/2019
ms.openlocfilehash: 83d4d0a60db4bdc112bb35bfbf61c0396646ad31
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989022"
---
# <a name="build-aspnet-core-22-applications-deployed-as-linux-containers-into-an-akskubernetes-orchestrator"></a>Vytvářejte ASP.NET aplikace Core 2.2 nasazené jako linuxové kontejnery do orchestrátoru AKS/Kubernetes

Azure Kubernetes Services (AKS) je spravované služby Orchestraations Kubernetes v Azure, které zjednodušují nasazení a správu kontejnerů.

AKS hlavní rysy jsou:

- Rovina ovládacího prvku hostované v Azure
- Automatické upgrady
- Samoopravení
- Uživatelsky konfigurovatelné škálování
- Jednodušší uživatelské prostředí pro vývojáře i operátory clusteru.

Následující příklady zkoumají vytvoření aplikace ASP.NET Core 2.2, která běží na Linuxu a nasadí se do clusteru AKS v Azure, zatímco vývoj se provádí pomocí Visual Studia 2017.

## <a name="creating-the-aspnet-core-22-project-using-visual-studio-2017"></a>Vytvoření projektu ASP.NET Jádra 2.2 pomocí Visual Studia 2017

ASP.NET Core je univerzální vývojová platforma spravovaná společností Microsoft a komunitou .NET na GitHubu. Je to multiplatformní, podporuje Windows, macOS a Linux a dá se používat ve scénářích zařízení, cloudu a embedded/IoT.

Tento příklad používá jednoduchý projekt, který je založen na šabloně webového rozhraní API sady Visual Studio, takže k vytvoření ukázky nepotřebujete žádné další znalosti. Projekt je třeba vytvořit pouze pomocí standardní šablony, která obsahuje všechny prvky pro spuštění malého projektu s rozhraním REST API pomocí technologie ASP.NET Core 2.2.

![Přidejte nové okno projektu v sadě Visual Studio a vyberte ASP.NET základní webovou aplikaci.](media/create-aspnet-core-application.png)

**Obrázek 4-36**. Vytváření ASP.NET základní aplikace

Chcete-li vytvořit ukázkový projekt v sadě Visual Studio, vyberte **možnost Soubor** > **nový** > **projekt**, vyberte typy **webových** projektů v levém podokně následované **ASP.NET základní webové aplikace**.

Visual Studio uvádí šablony pro webové projekty. V našem příkladu vyberte **rozhraní API** a vytvořte ASP.NET webovou aplikaci rozhraní API.

Ověřte, zda jste jako framework vybrali ASP.NET Core 2.2. .NET Core 2.2 je součástí poslední verze Visual Studia 2017 a je automaticky nainstalován a nakonfigurován pro vás při instalaci Sady Visual Studio 2017.

![Visual Studio dialogové okno pro výběr typu ASP.NET základní webové aplikace s vybranou možností rozhraní API.](media/create-web-api-application.png)

**Obrázek 4-37**. Výběr ASP.NET typu projektu CORE 2.2 a Web API

Pokud máte předchozí verzi rozhraní .NET Core, můžete si stáhnout <https://dotnet.microsoft.com/download>a nainstalovat verzi 2.2 z aplikace .

Podporu Dockeru můžete přidat při vytváření projektu nebo později, takže můžete "Dockerize" váš projekt kdykoli. Chcete-li přidat podporu Dockeru po vytvoření projektu, klikněte pravým tlačítkem myši na uzel projektu v Průzkumníku řešení a v místní nabídce vyberte **Přidat** > **podporu Dockeru.**

![Možnost kontextové nabídky pro přidání podpory Dockeru do existujícího projektu: Klikněte pravým tlačítkem myši (na projektu) > Přidat podporu > Dockeru.](media/add-docker-support-to-project.png)

**Obrázek 4-38**. Přidání podpory Dockeru do existujícího projektu

Chcete-li dokončit přidání podpory Dockeru, můžete si vybrat Windows nebo Linux. V takovém případě vyberte **Linux**, protože AKS nepodporuje kontejnery Windows (ke konci roku 2018).

![Dialogové okno Možnosti pro výběr cílového operačního systému pro dockerfile.](media/select-linux-docker-support.png)

**Obrázek 4-39**. Výběr linuxových kontejnerů.

S těmito jednoduchými kroky máte ASP.NET aplikaci Core 2.2 spuštěnou v kontejneru Linuxu.

Jak můžete vidět, integrace mezi Visual Studio 2017 a Dockerem je zcela orientována na produktivitu vývojáře.

Nyní můžete aplikaci spustit pomocí klávesy **F5** nebo pomocí tlačítka **Přehrát.**

Po spuštění projektu můžete vypsat `docker images` obrázky pomocí příkazu. Měli byste `mssampleapplication` vidět image vytvořenou automatickým nasazením našeho projektu s Visual Studio 2017.

```console
docker images
```

![Výstup konzoly z příkazu image dockeru zobrazuje seznam s: Úložiště, Značka, ID obrázku, Vytvořeno (datum) a Velikost.](media/docker-images-command.png)

**Obrázek 4-40**. Zobrazení i0 bitových kopií Dockeru

## <a name="register-the-solution-in-the-azure-container-registry"></a>Registrace řešení v registru kontejnerů Azure

Nahrajte image do libovolného registru Dockeru, jako je [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) nebo Docker Hub, takže image se dá nasadit do clusteru AKS z tohoto registru. V takovém případě nahráváme image do registru kontejnerů Azure.

### <a name="create-the-image-in-release-mode"></a>Vytvoření obrazu v režimu vydání

Nyní vytvoříme obrázek v režimu **vydání** (připraven k výrobě) změnou na **verzi**, jak je znázorněno na obrázku 4-41, a spuštěním aplikace jako předtím.

![Možnost panelu nástrojů ve VS pro sestavení v režimu vydání.](media/select-release-mode.png)

**Obrázek 4-41**. Výběr režimu vydání

Pokud spustíte `docker image` příkaz, uvidíte oba vytvořené obrazy, jeden `release` pro a druhý pro `debug` režim.

### <a name="create-a-new-tag-for-the-image"></a>Vytvoření nové značky pro obrázek

Každá bitová kopie kontejneru `loginServer` musí být označena názvem registru. Tato značka se používá pro směrování při nahrávání imagí kontejneru do registru imagí.

Název můžete `loginServer` zobrazit z portálu Azure, přičemž informace z registru kontejnerů Azure

![Zobrazení prohlížeče názvu registru kontejneru Azure, v pravém horním rohu.](media/loginServer-name.png)

**Obrázek 4-42**. Zobrazení názvu registru

Nebo spuštěním následujícího příkazu:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup konzoly z výše uvedeného příkazu.](media/az-cli-loginServer-name.png)

**Obrázek 4-43**. Získání názvu registru pomocí prostředí PowerShell

V obou případech získáte název. V našem `mssampleacr.azurecr.io`příkladu .

Nyní můžete označit obrázek, přičemž nejnovější obrázek (release image), s příkazem:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Po spuštění `docker tag` příkazu uveďte `docker images` obrázky pomocí příkazu a obrázek byste měli vidět s novou značkou.

![Výstup konzoly z příkazu image dockeru.](media/tagged-docker-images-list.png)

**Obrázek 4-44**. Zobrazení tagovaných obrázků

### <a name="push-the-image-into-the-azure-acr"></a>Zasunutí image do Azure ACR

Přihlášení do registru kontejnerů Azure

```console
az acr login --name mssampleacr
```

Zatlačte image do Azure ACR pomocí následujícího příkazu:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Tento příkaz chvíli trvá, než obrázky nahraje, ale poskytne vám zpětnou vazbu.

![Výstup konzoly z příkazu push dockeru: zobrazuje pruh průběhu založený na znaku pro každou vrstvu.](media/uploading-image-to-acr.png)

**Obrázek 4-45**. Nahrání obrázku do ACR

Níže můžete vidět výsledek, který byste měli získat po dokončení procesu:

![Výstup konzoly z příkazu push dockeru, dokončený, zobrazující všechny hladiny nebo uzly.](media/uploading-docker-images-complete.png)

**Obrázek 4-46**. Zobrazení uzlů

Dalším krokem je nasazení kontejneru do clusteru AKS Kubernetes. K tomu potřebujete soubor (**.yml deploy file),** který obsahuje následující:

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
> Další informace o nasazení s Kubernetes naleznete v:<https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Nyní jste téměř připraveni k nasazení pomocí **Kubectl**, ale nejprve musíte získat pověření do clusteru AKS pomocí tohoto příkazu:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Výstup konzoly z výše uvedeného příkazu: Sloučený "MSSampleK8Cluster jako aktuální kontext v /root/.kube/config](media/getting-aks-credentials.png)

**Obrázek 4-47**. získání přihlašovacích údajů

Potom pomocí `kubectl create` příkazu spusťte nasazení.

```console
kubectl create -f mssample-deploy.yml
```

![Konzolový výstup z výše uvedeného příkazu: nasazení "mssamplesbook" vytvořen. služba "mssample-kub-app" vytvořena.](media/kubectl-create-command.png)

**Obrázek 4-48**. Nasazení do Kubernetes

Po dokončení nasazení můžete přistupovat ke konzoli Kubernetes pomocí místního proxy serveru, ke kterému můžete dočasně přistupovat pomocí tohoto příkazu:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

A přístup k `http://127.0.0.1:8001`url .

![Zobrazení prohlížeče řídicího panelu Kubernetes zobrazující nasazení, pody, sady replik a služby.](media/kubernetes-cluster-information.png)

**Obrázek 4-49**. Zobrazit informace o clusteru Kubernetes

Teď máte aplikaci nasazenou v Azure pomocí linuxového kontejneru a clusteru AKS Kubernetes. K procházení aplikace můžete přistupovat k veřejné IP adrese vaší služby, kterou můžete získat z portálu Azure.

> [!NOTE]
> Můžete vidět, jak vytvořit clusterAKS pro tuto ukázku v části [**Nasazení do služby Azure Kubernetes (AKS)**](deploy-azure-kubernetes-service.md) v této příručce.

>[!div class="step-by-step"]
>[Předchozí](set-up-windows-containers-with-powershell.md)
>[další](../docker-devops-workflow/index.md)
