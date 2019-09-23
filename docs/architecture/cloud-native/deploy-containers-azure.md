---
title: Nasazení kontejnerů v Azure
description: Nasazení kontejnerů v Azure pomocí Azure Container Registry služby Azure Kubernetes a Azure Dev Spaces.
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183264"
---
# <a name="deploying-containers-in-azure"></a>Nasazení kontejnerů v Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Kontejnery poskytují mnoho výhod, z nichž jeden je přenositelnost. Můžete snadno použít stejný kontejner, který jste vytvořili a otestovali místně, a nasadit ho do Azure, kde může spustit vaši aplikaci v pracovním a produkčním prostředí. Azure poskytuje řadu možností pro hostování aplikací založených na kontejnerech a podobně podporuje několik různých způsobů nasazení. Nejběžnější a nejpružnější přístup je nasazení vašich kontejnerů do Azure Container Registry (ACR), kde jsou přístupné pro všechny služby, které chcete používat k hostování. Azure Web App for Containers, Azure Kubernetes Services (AKS) a Azure Container instance (ACI) mají přístup k imagím kontejneru, které byly vloženy do ACR.

## <a name="azure-container-registry"></a>Azure Container Registry

Azure Container Registry (ACR) umožňuje sestavovat, ukládat a spravovat image pro všechna vaše nasazení kontejnerů. Existují další registry kontejnerů, veřejné i privátní, na které můžete nasazovat kontejnery. Výhodou ACR nad jinými možnostmi je, že vaše image se můžou uchovávat v produkčním prostředí, což zlepšuje dobu sestavování a nasazování. Můžete je také zabezpečit pomocí stejných postupů zabezpečení, které používáte pro ostatní prostředky Azure, což zlepšuje zabezpečení a snižuje úsilí při správě prostředků.

[Registr kontejnerů vytvoříte pomocí webu Azure Portal](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal) nebo [pomocí Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli) nebo [nástrojů PowerShellu](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell). Vytvoření nového registru kontejnerů vyžaduje jenom předplatné Azure, skupinu prostředků a jedinečný název. Obrázek 3-11 ukazuje základní možnosti pro vytvoření registru, který bude hostovaný v *registru registru*. azurecr.IO.

![Vytvořte kontejner registru](./media/create-container-registry.png)
kontejneru**3-11**. Vytvoření registru kontejnerů

Po vytvoření registru ho budete muset ověřit, abyste ho mohli použít. Obvykle se k registru přihlašujete pomocí příkazu Azure CLI:

```azurecli
az acr login --name *registryname*
```

Po vytvoření registru v Azure Container Registry můžete k vložení imagí kontejneru do něj použít příkazy Docker. Předtím, než to uděláte, musíte nejdřív označit Image pomocí plně kvalifikovaného názvu (URL) přihlašovacího serveru ACR. Tato akce bude mít formát *Registry*. azurecr.IO.

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

Vývojáři by měli do registru kontejneru vkládat jenom zřídka přímo ze svých počítačů. Místo toho by měl být pro tento proces zodpovědný kanál sestavení definovaný nástrojem jako Azure DevOps. Další informace najdete v [kapitole DevOps v nativním cloudu](devops.md).

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

Pokud vaše aplikace založené na kontejnerech zahrnuje více kontejnerů, pravděpodobně budete chtít definovat a spravovat interakce mezi kontejnery pomocí nástroje *Orchestrator* , jako je Kubernetes. Po nasazení imagí kontejneru na ACR můžete snadno nakonfigurovat služby Azure Kubernetes na automatické nasazení aktualizovaných imagí z ACR. Když zadáte úplný kanál CI/CD, můžete nakonfigurovat strategii pro [Kanárské verze](https://martinfowler.com/bliki/CanaryRelease.html) , aby se minimalizovalo riziko při rychlém nasazování aktualizací. Tato nová verze aplikace se zpočátku nakonfiguruje v produkčním prostředí, takže se na ni nesměruje žádný provoz a malý počet uživatelů se směruje do nově nasazené verze aplikace. Protože tým získá v nové verzi softwaru důvěru, další instance nové verze se zavádějí do vyřazení instancí předchozí verze. AKS snadno podporuje tento styl nasazení.

Stejně jako u většiny prostředků v Azure můžete vytvořit clustery Azure Kubernetes pomocí portálu nebo pomocí nástrojů příkazového řádku nebo nástrojů pro automatizaci infrastruktury, jako je Helm nebo Terraformu. Chcete-li začít s novým clusterem, je nutné zadat následující informace:

- Předplatné Azure
- Resource group
- Název clusteru Kubernetes
- Oblast
- Verze Kubernetes
- Předpona názvu DNS
- Velikost uzlu
- Počet uzlů

Tyto informace jsou dostatečné k tomu, aby bylo možné začít. V rámci procesu vytváření na webu Azure Portal můžete také nakonfigurovat možnosti pro následující funkce clusteru:

- Škálování
- Ověřování
- Síťové služby
- Monitorování
- Značky

Tento [rychlý Start vás provede nasazením clusteru AKS pomocí Azure Portal](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal).

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Komplexní clustery Kubernetes můžou vyžadovat, aby hostitelé měli významné prostředky, což může ztížit vývojářům spustit celou aplikaci na jednom počítači (hlavně notebook). Azure Dev Spaces nabízí řešení, které vývojářům umožní pracovat s vlastními verzemi clusterů Azure Kubernetes hostovaných v Azure. Azure Dev Spaces je navržený tak, aby usnadnil vývoj aplikací založených na mikroslužbách pomocí AKS.

Abychom porozuměli hodnotě Azure Dev Spaces, umožněte mi, aby mě Nasdílela tuto nabídku z Gabe Monroy, odpoledne v kontejnerech na Microsoft Azure:

"Představte si, že jste nový zaměstnanec, který se snaží opravit chybu v komplexní aplikaci mikroslužeb skládající se z desítek komponent, z nichž každá má vlastní konfiguraci a záložní služby. Abyste mohli začít, musíte nakonfigurovat své místní vývojové prostředí tak, aby mohlo napodobovat produkci, včetně nastavení IDE, řetězu nástrojů, kontejnerových závislostí služby, místního prostředí Kubernetes, pokládání pro záložní služby a další. V případě, že se při nastavení vývojového prostředí nastavila tato první chyba, může to trvat několik dní.

> Nebo můžete použít vývojové prostory a AKS. "

Proces pro práci s Azure Dev Spaces zahrnuje následující kroky:

1. Vytvořte prostor pro vývoj.
2. Nakonfigurujte kořenový prostor pro vývoj.
3. Nakonfigurujte podřízený prostor pro vývoj (pro vaši vlastní verzi systému).
4. Připojte se k prostoru pro vývoj.

Všechny tyto kroky můžete provést pomocí Azure CLI a nových `azds` nástrojů příkazového řádku. Například pro vytvoření nového vývojového prostoru Azure pro určitý cluster Kubernetes byste měli použít příkaz podobný tomuto:

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

Dále můžete pomocí `azds prep` příkazu vygenerovat potřebné prostředky Docker a graf Helm pro spuštění aplikace. Pak spustíte kód v AKS pomocí `azds up`. Při prvním spuštění tohoto příkazu se nainstaluje graf Helm a kontejnery se sestaví a nasadí podle vašich pokynů. Při prvním spuštění může trvat několik minut. Po provedení změn se ale můžete připojit k vlastnímu vývojovému prostoru pro vývoj pomocí `azds space select` a pak nasadit a ladit vaše aktualizace v izolovaném prostředí pro vývoj v izolovaném prostoru. Jakmile budete mít prostředí pro vývoj v provozu, můžete k němu odeslat aktualizace tak, že znovu `azds up` vydáte příkaz nebo můžete použít integrované nástroje v aplikaci Visual Studio nebo Visual Studio Code. Pomocí VS Code se ke svému vývojovému prostoru připojíte pomocí palety příkazů. Obrázek 3-12 ukazuje, jak spustit webovou aplikaci pomocí Azure Dev Spaces v aplikaci Visual Studio.

![Připojení k Azure dev Spaces v aplikaci Visual](./media/azure-dev-spaces-visual-studio-launchsettings.png)
Studio**Obrázek 3-12**. Připojení k Azure Dev Spaces v aplikaci Visual Studio

## <a name="references"></a>Odkazy

- [Kanárské verze](https://martinfowler.com/bliki/CanaryRelease.html)
- [Azure Dev Spaces s VS Code](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [Azure Dev Spaces se sadou Visual Studio](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
>[Předchozí](combine-containers-serverless-approaches.md)
>[Další](scale-containers-serverless.md)
