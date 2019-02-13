---
title: Sestavení aplikace ASP.NET Core 2.1 nasazené jako kontejnery Linux do clusterů AKS/Kubernetes
description: Životní cyklus aplikace kontejnerizovaných Dockeru s platformou a nástroji Microsoft
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: b03b6fab9dcd53e97c2bc4d7e5c958ca4b931077
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/13/2019
ms.locfileid: "56221388"
---
# <a name="build-aspnet-core-21-applications-deployed-as-linux-containers-into-akskubernetes-orchestrator"></a>Sestavení aplikace ASP.NET Core 2.1 nasazené jako kontejnery Linux do produktu orchestrator AKS/Kubernetes

Služby Azure Kubernetes (AKS) je spravované Kubernetes Orchestrace služeb Azure, které zjednodušují nasazování kontejnerů a správu.

AKS hlavní funkce patří:

- Rovina řízení hostovanou v Azure
- Automatizované upgrady
- Opravy
- Uživatel konfigurovatelné škálování
- Jednodušší uživatelské prostředí pro vývojáře i operátory clusteru.

Následující příklady prozkoumat vytvoření aplikace ASP.NET Core 2.1, která běží na Linuxu a nasadí do clusteru AKS v Azure, zatímco probíhá vývoj pomocí sady Visual Studio 2017.

## <a name="creating-the-aspnet-core-21-project-using-visual-studio-2017"></a>Vytváří se projekt ASP.NET Core 2.1 pomocí sady Visual Studio 2017

ASP.NET Core je pro obecné účely Vývojová platforma udržuje od Microsoftu a komunity .NET na Githubu. Je multiplatformní, podpora Windows, macOS a Linux a je možné v zařízení, cloud a scénáře vložené a IoT.

Tento příklad používá jednoduchý projekt, který je založen na základě Visual Studio webového rozhraní API šablony, takže není nutné žádné další znalostní báze k vytvoření vzorku. Stačí vytvořit projekt pomocí standardní šablonu, která obsahuje všechny prvky malém projektu pomocí rozhraní REST API, technologií ASP.NET Core 2.1.

![Přidáte okno nového projektu v sadě Visual Studio, vyberte webovou aplikaci ASP.NET Core.](media/create-aspnet-core-application.png)

**Obrázek 4 – 36**. Vytvoření aplikace ASP.NET Core

K vytvoření ukázkového projektu, je nutné vybrat **souboru** > **nový** > **projektu** v sadě Visual Studio. Pak zobrazí seznam šablon pro několik typů projektů, kdy musíte Hledat **webové** > **.NET Core** na levém panelu. V tomto příkladu vyberte **webové aplikace ASP.NET Core**.

V dalším dialogovém okně ověřte, že jste zvolili .NET Core a ASP.NET Core 2.1 jako cílové rozhraní v horní pulldowns, jak je znázorněno na obrázku 4-37 a potom výběrem možnosti rozhraní API k vytvoření aplikace webového rozhraní API ASP.NET Core.

.NET Core 2.1 je zahrnuté v sadě Visual Studio 2017 verze 15.7.0 nebo vyšší a je automaticky nainstalován a nakonfigurován pro vás, když vyberete **vývoj pro různé platformy .NET Core** úloh během instalace.

![Visual Studio dialogové okno pro výběr typu webové aplikace ASP.NET Core s vybranou možností rozhraní API.](media/create-web-api-application.png)

**Obrázek 4-37**. Typ projektu výběrem ASP.NET CORE 2.1 a webového rozhraní API

Pokud máte jakékoli předchozí verze .NET Core, můžete stáhnout a nainstalovat z verze 2.1 <https://www.microsoft.com/net/download/core#/sdk>.

Při vytváření projektu v předchozím kroku, nebo později v případě potřeby po spuštění projektu můžete přidat podporu Dockeru. Chcete-li přidat podporu Dockeru po vytvoření projektu, klikněte pravým tlačítkem na soubor projektu v **Průzkumníka řešení** a vyberte **přidat** > **podporu Dockeru** na kontextové nabídky.

![Možnost místní nabídky do existujícího projektu přidat podporu Dockeru: Klikněte pravým tlačítkem (na projekt) > Přidat > podpory Dockeru.](media/add-docker-support-to-project.png)

**Obrázek 4-38**. Přidání podpory Dockeru do existujícího projektu

Abyste mohli dokončit přidávání podpory Docker, budete mít možnost Windows nebo Linux. V tomto případě vyberte **Linux**, protože služba AKS nepodporuje kontejnery Windows (jako opožděné 2018).

![Dialogové okno Možnosti a vyberte cílový operační systém pro soubor Dockerfile.](media/select-linux-docker-support.png)

**Obrázek 4-39**. Výběr kontejnery Linuxu.

Pomocí tohoto jednoduchého postupu bude mít vaše aplikace ASP.NET Core 2.1 běžící v kontejneru Linuxu.

Jak vidíte, je zcela orientovaný produktivity pro vývojáře integraci mezi Visual Studio 2017 a Dockeru.

Nyní můžete stisknout **F5** sestavíte a spustíte aplikaci.

Po spuštění projektu, můžete vytvořit seznam imagí pomocí `docker images` příkazu. Měli byste vidět `mssampleapplication` image vytvořené pomocí automatického nasazení našich projekt pomocí sady Visual Studio 2017.

```console
docker images
```

![Výstup konzoly z příkazu imagí dockeru, zobrazí se seznam s: Úložiště, značky, ID bitové kopie, vytvořeno (datum) a velikost.](media/docker-images-command.png)

**Obrázek 4 – 40**. Zobrazení imagí Dockeru

## <a name="register-the-solution-in-the-azure-container-registry"></a>Zaregistrujte toto řešení v Azure Container Registry

Tuto image odeslat do jakéhokoli registru Dockeru, jako je třeba [Azure Container Registry (ACR)](https://azure.microsoft.com/services/container-registry/) nebo Docker Hubu, Image se dají nasadit do clusteru AKS z tohoto registru. V tomto případě jsme už nahráním image do služby Azure Container Registry.

### <a name="create-the-image-in-release-mode"></a>Vytvoření bitové kopie v režimu vydání

Vytvoření bitové kopie v **vydání** režimu (připravena na produkční prostředí) změna na verzi, jak je znázorněno zde a stisknutím klávesy F5 spusťte aplikaci znovu.

![Možnosti panelu nástrojů v sadě Visual Studio vytvářet v režimu vydání.](media/select-release-mode.png)

**Obrázek 4 – 41**. Výběr režimu vydání

Pokud je spuštěn `docker image` příkaz, zobrazí se vám i obrázky vytvořené. Jeden pro `debug` a druhou pro `release` režimu.

### <a name="create-a-new-tag-for-the-image"></a>Vytvořit novou značku pro bitovou kopii

Každá image kontejneru musí být s klíčovým slovem `loginServer` název registru. Tato značka se používá pro směrování při nahrávání imagí kontejneru do registru imagí.

Můžete zobrazit `loginServer` jméno z portálu Azure portal, přičemž informace ze služby Azure Container Registry

![Zobrazení prohlížeče s názvem registru kontejnerů Azure, v pravém horním rohu.](media/loginServer-name.png)

**Obrázek 4-42**. Zobrazit název registru

Nebo spuštěním následujícího příkazu:

```console
az acr list --resource-group MSSampleResourceGroup --query "[].{acrLoginServer:loginServer}" --output table
```

![Výstup z výše uvedeného příkazu konzoly.](media/az-cli-loginServer-name.png)

**Obrázek 4-43**. Získejte název registru pomocí Powershellu

V obou případech získáte název. V našem příkladu `mssampleacr.azurecr.io`.

Teď můžete označit image, přičemž nejnovější image (verze image), pomocí následujícího příkazu:

```console
docker tag mssampleaksapplication:latest mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Po spuštění `docker tag` příkazu, výpis všech imagí s `docker images` příkazu. Měli byste vidět na obrázku s novou značku.

![Výstup z příkazu imagí dockeru konzoly.](media/tagged-docker-images-list.png)

**Obrázek 4 – 44**. Zobrazení označených imagí

### <a name="push-the-image-into-the-azure-acr"></a>Nahrání image do služby ACR Azure

Nahrání image do služby ACR Azure, pomocí následujícího příkazu:

```console
docker push mssampleacr.azurecr.io/mssampleaksapplication:v1
```

Tento příkaz chvíli trvat, než nahrání imagí, ale poskytuje zpětnou vazbu v procesu.

![Výstupu z příkazu push docker konzoly: zobrazuje indikátor průběhu znakový pro jednotlivé úrovně.](media/uploading-image-to-acr.png)

**Obrázek 4-45**. Nahrání image služby ACR

Můžete vidět dole výsledek, že by vám měl po dokončení procesu:

![Výstup z dockeru push příkazu, dokončeno, zobrazující všechny vrstvy nebo uzlů konzoly.](media/uploading-docker-images-complete.png)

**Obrázek 4 – 46**. Zobrazení uzlů

Dalším krokem je nasazení kontejneru do vašeho clusteru AKS Kubernetes. K tomu budete potřebovat soubor (**nasaďte soubor .yml**), v tomto případě obsahuje:

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
        - mane: mssample-services-app
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
> Další informace o nasazení s využitím Kubernetes najdete v článku: <https://kubernetes.io/docs/reference/kubectl/cheatsheet/>

Nyní jste téměř připraveni k nasazení pomocí **Kubectl**, ale nejprve musíte získat přihlašovací údaje ke clusteru AKS pomocí tohoto příkazu:

```console
az aks get-credentials --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

![Výstup z výše uvedeného příkazu konzoly: Sloučené "MSSampleK8Cluster jako aktuální kontext v /root/.kube/config](media/getting-aks-credentials.png)

**Obrázek 4-47**. získání přihlašovacích údajů

Potom použijte `kubectl create` příkaz ke spuštění nasazení.

```console
kubectl create -f mssample-deploy.yml
```

![Konzole výstup z výše uvedeného příkazu: "mssamplesbook" vytvoří nasazení. Služba "mssample-kub-app" vytvořili.](media/kubectl-create-command.png)

**Obrázek 4 – 48**. Nasazení do Kubernetes

Po dokončení nasazení můžete přístup ke konzole Kubernetes s místní proxy server, ke kterému jste dočasně přístup pomocí tohoto příkazu:

```console
az aks browse --resource-group MSSampleResourceGroupAKS --name mssampleclusterk801
```

A přístup k adresu url `http://127.0.0.1:8001`.

![Zobrazení prohlížeče s řídicí panel Kubernetes, včetně nasazení, Podů, sady replik a služeb.](media/kubernetes-cluster-information.png)

**Obrázek 4-49**. Zobrazit informace o clusteru Kubernetes

Teď máte aplikaci nasazenou na Azure pomocí kontejneru Linuxu a Kubernetes Cluster ve službě AKS. Můžete přistupovat k vaší aplikace na veřejné IP adresy vaší služby, který můžete získat z webu Azure portal.

> [!NOTE]
> Zobrazí se postup vytvoření clusteru AKS pro tuto ukázku v části [ **nasadit do Azure Kubernetes Service (AKS)** ](deploy-azure-kubernetes-service.md) v této příručce.

>[!div class="step-by-step"]
>[Předchozí](set-up-windows-containers-with-powershell.md)
>[další](../docker-devops-workflow/index.md)
