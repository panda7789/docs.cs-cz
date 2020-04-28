---
title: Nasazení kontejnerů v Azure
description: Nasazení kontejnerů v Azure pomocí Azure Container Registry, služby Azure Kubernetes a Azure Dev Spaces.
ms.date: 04/13/2020
ms.openlocfilehash: 6238460c6129583c34e6b328c38ed9042f32f3d6
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199557"
---
# <a name="deploying-containers-in-azure"></a>Nasazení kontejnerů v Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V této kapitole jsme probrali kontejnery a v kapitole 1. Zjistili jsme, že kontejnery poskytují spoustu výhod aplikacím nativním pro Cloud, včetně přenositelnosti. V cloudu Azure můžete nasadit stejné kontejnerové služby v rámci pracovních a produkčních prostředí. Azure poskytuje několik možností pro hostování těchto kontejnerových úloh:

- Služby Azure Kubernetes (AKS)
- Azure Container Instance (ACI)
- Azure Web Apps pro kontejnery

## <a name="azure-container-registry"></a>Azure Container Registry

Při uzavřeníí mikroslužby nejprve vytvoří kontejner sestavení "image". Obrázek je binární reprezentace kódu služby, závislosti a modulu runtime. I když můžete vytvořit image ručně pomocí `Docker Build` příkazu z rozhraní Docker API, lepší přístup je vytvořit jako součást procesu automatizovaného sestavení.

Po vytvoření se image kontejneru ukládají do registrů kontejnerů. Umožňují vytvářet, ukládat a spravovat image kontejnerů. K dispozici je mnoho registrů, veřejný i privátní. Azure Container Registry (ACR) je plně spravovaná služba registrů kontejnerů v cloudu Azure. Ukládá vaše image do sítě Azure a zkracuje čas jejich nasazení na hostitele kontejnerů Azure. Můžete je také zabezpečit pomocí stejných postupů zabezpečení a identity, které používáte pro jiné prostředky Azure.

Azure Container Registry vytvoříte pomocí nástrojů [Azure Portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal), [Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli)nebo [PowerShellu](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell). Vytvoření registru v Azure je jednoduché. Vyžaduje předplatné Azure, skupinu prostředků a jedinečný název. Obrázek 3-11 ukazuje základní možnosti pro vytvoření registru, který bude hostovaný na adrese `registryname.azurecr.io`.

![Vytvoření registru kontejneru](./media/create-container-registry.png)

**Obrázek 3-11**. Vytvoření registru kontejneru

Po vytvoření registru ho budete muset ověřit, abyste ho mohli použít. Obvykle se k registru přihlašujete pomocí příkazu Azure CLI:

```azurecli
az acr login --name *registryname*
```

Po ověření můžete k vložení imagí kontejneru do něj použít příkazy Docker. Předtím, než to uděláte, musíte si image označit pomocí plně kvalifikovaného názvu (URL) přihlašovacího serveru ACR. Bude mít formát *Registry*. azurecr.IO.

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

Po označení obrázku použijte `docker push` příkaz k nahrání image do instance ACR.

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

Po nahrání image do registru je vhodné odebrat image z místního prostředí Docker pomocí tohoto příkazu:

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

V rámci osvědčeného postupu vývojáři neměli ručně nasdílet image do registru kontejneru. Místo toho by měl být pro tento proces zodpovědný kanál sestavení definovaný nástrojem jako GitHub nebo Azure DevOps. Další informace najdete v [kapitole DevOps v nativním cloudu](devops.md).

## <a name="acr-tasks"></a>Úlohy ACR

[ACR úkoly](https://docs.microsoft.com/azure/container-registry/container-registry-tasks-overview) jsou sadou funkcí dostupných z Azure Container Registry. Rozšiřuje [cyklus vývoje vnitřních smyček](https://docs.microsoft.com/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow) tím, že vytváří a spravuje image kontejnerů v cloudu Azure. Namísto vyvolání `docker build` a `docker push` místního nasazení na vašem vývojovém počítači jsou automaticky zpracovány ACR úkoly v cloudu.

Pomocí příkazu AZ CLI sestavíte image kontejneru a nahrajete ji do ACR:

```azurecli
# create a container registry
az acr create --resource-group myResourceGroup --name myContainerRegistry008 --sku Basic

# build container image in ACR and push it into your container regsitry
az acr build --image sample/hello-world:v1  --registry myContainerRegistry008 --file Dockerfile .
```

Jak vidíte z předchozího bloku příkazu, není nutné instalovat Docker Desktop do vývojového počítače. Kromě toho můžete nakonfigurovat triggery úloh ACR k opětovnému sestavení imagí kontejnerů ve zdrojovém kódu i v základních aktualizacích imagí.

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

V této kapitole jsme probrali službu Azure Kubernetes Service (AKS) s délkou. Zjistili jsme, že jde o de facto kontejner Orchestrator, který spravuje kontejnerové nativní aplikace pro Cloud.

Po nasazení bitové kopie do registru, jako je například ACR, můžete nakonfigurovat AKS na automatické vyžádání a nasazení. Díky kanálu CI/CD můžete nakonfigurovat strategii pro [Kanárské verze](https://martinfowler.com/bliki/CanaryRelease.html) , aby se minimalizovalo riziko při rychlém nasazování aktualizací. Tato nová verze aplikace se zpočátku nakonfiguruje v produkčním prostředí a nesměruje na ni žádný provoz. Systém pak bude směrovat malé procento uživatelů na nově nasazenou verzi. Vzhledem k tomu, že tým získá důvěru v nové verzi, může kumulativní a vyřazení starých instancí. AKS snadno podporuje tento styl nasazení.

Stejně jako u většiny prostředků v Azure můžete vytvořit cluster služby Azure Kubernetes pomocí portálu, příkazového řádku nebo nástrojů pro automatizaci, jako je Helm nebo Terraformu. Chcete-li začít s novým clusterem, je nutné zadat následující informace:

- Předplatné Azure
- Skupina prostředků
- Název clusteru Kubernetes
- Oblast
- Verze Kubernetes
- Předpona názvu DNS
- Velikost uzlu
- Počet uzlů

Tyto informace jsou dostatečné k tomu, aby bylo možné začít. V rámci procesu vytváření v Azure Portal můžete také nakonfigurovat možnosti pro následující funkce clusteru:

- Měřítko
- Authentication
- Sítě
- Monitorování
- Značky

Tento [rychlý Start vás provede nasazením clusteru AKS pomocí Azure Portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Nativní aplikace pro Cloud můžou rychle rozšiřovat rozsáhlé a komplexní a vyžadují, aby se mohly spustit významné výpočetní prostředky. V těchto scénářích nemůže být celá aplikace hostována na vývojovém počítači (zejména notebook). Azure Dev Spaces je navržený pro řešení tohoto problému pomocí AKS. Umožňuje vývojářům pracovat s místní verzí svých služeb a současně hostovat zbytek aplikace v AKS vývojovém clusteru.

Vývojáři sdílejí běžící (vývojovou) instanci v clusteru AKS, který obsahuje celou kontejnerovou aplikaci. Ale používají osobní prostory nastavené na svém počítači k místnímu vývoji svých služeb. Po dokončení se otestuje z konce na konec v clusteru AKS – bez závislostí replikace. Azure Dev Spaces sloučí kód z místního počítače se službami v AKS. Vývojáři můžou rychle iterovat a ladit kód přímo v Kubernetes pomocí sady Visual Studio nebo Visual Studio Code.

Abychom porozuměli hodnotě Azure Dev Spaces, umožněte mi, aby mě Nasdílela tuto nabídku z Gabe Monroy, odpoledne v kontejnerech na Microsoft Azure:

> Představte si, že jste nový zaměstnanec, který se snaží opravit chybu v komplexní aplikaci mikroslužeb skládající se z desítek komponent, z nichž každý má vlastní konfiguraci a službu back-in. Abyste mohli začít, musíte nakonfigurovat své místní vývojové prostředí tak, aby mohlo napodobovat produkci, včetně nastavení IDE, řetězu nástrojů, kontejnerových závislostí služby, místního prostředí Kubernetes, pokládání pro záložní služby a další. V případě, že se při nastavení vývojového prostředí nastavila tato první chyba, může to trvat několik dní.
> Nebo můžete použít vývojové prostory a AKS.

Proces pro práci s Azure Dev Spaces zahrnuje následující kroky:

1. Vytvořte prostor pro vývoj.
2. Nakonfigurujte kořenový prostor pro vývoj.
3. Nakonfigurujte podřízený prostor pro vývoj (pro vaši vlastní verzi systému).
4. Připojte se k prostoru pro vývoj.

Všechny tyto kroky můžete provést pomocí Azure CLI a nových `azds` nástrojů příkazového řádku. Například pro vytvoření nového vývojového prostoru Azure pro určitý cluster Kubernetes byste měli použít příkaz podobný tomuto:

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Dále můžete pomocí `azds prep` příkazu vygenerovat potřebné prostředky Docker a graf Helm pro spuštění aplikace. Pak spustíte kód v AKS pomocí `azds up`. Při prvním spuštění tohoto příkazu se nainstaluje graf Helm. Kontejnery se sestaví a nasadí podle vašich pokynů. Při prvním spuštění této úlohy může trvat několik minut. Po provedení změn se ale můžete připojit k vlastnímu vývojovému prostoru pro vývoj pomocí `azds space select` a pak nasadit a ladit vaše aktualizace v izolovaném prostředí pro vývoj v izolovaném prostoru. Jakmile budete mít vývojové prostředí v provozu, můžete k němu odeslat aktualizace opětovným vyvoláním `azds up` příkazu nebo můžete použít integrované nástroje v aplikaci Visual Studio nebo Visual Studio Code. Pomocí VS Code se ke svému vývojovému prostoru připojíte pomocí palety příkazů. Obrázek 3-12 ukazuje, jak spustit webovou aplikaci pomocí Azure Dev Spaces v aplikaci Visual Studio.

![Připojení k Azure dev Spaces v aplikaci Visual](./media/azure-dev-spaces-visual-studio-launchsettings.png)
Studio**Obrázek 3-12**. Připojení k Azure Dev Spaces v aplikaci Visual Studio

>[!div class="step-by-step"]
>[Předchozí](combine-containers-serverless-approaches.md)
>[Další](scale-containers-serverless.md)
