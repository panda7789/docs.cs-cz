---
title: Škálování kontejnerů a bezserverových aplikací
description: Škálování aplikací v cloudu pomocí služby Azure Kubernetes, aby splňovala požadavky uživatelů
ms.date: 05/13/2020
ms.openlocfilehash: a5e1e8df785fd08901d9be41c0a06db35e09296b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613717"
---
# <a name="scaling-containers-and-serverless-applications"></a>Škálování kontejnerů a bezserverových aplikací

Existují dva způsoby, jak aplikaci škálovat: nahoru nebo ven. Předchozí odkazuje na přidání kapacity k jednomu prostředku, zatímco druhá odkazuje na přidání dalších prostředků ke zvýšení kapacity.

## <a name="the-simple-solution-scaling-up"></a>Jednoduché řešení: škálování

Upgrade existujícího hostitelského serveru se zvýšeným využitím procesoru, paměti, rychlosti v/v disku a rychlostí v/v sítě se označuje jako horizontální *navýšení*kapacity. Horizontální navýšení kapacity cloudové aplikace zahrnuje výběr více možností prostředků od dodavatele cloudu. Můžete například vytvořit nový fond uzlů s většími virtuálními počítači v clusteru Kubernetes. Pak migrujte své kontejnerové služby do nového fondu.

Aplikace bez serveru se škálují až po výběru velikosti prémiových [funkcí](https://docs.microsoft.com/azure/azure-functions/functions-scale) nebo velikostí instancí Premium z vyhrazeného plánu služby App Service.

## <a name="scaling-out-cloud-native-apps"></a>Horizontální navýšení kapacity cloudových aplikací

Nativní aplikace pro Cloud mají často zkušenosti s velkými výkyvy na vyžádání a vyžadují škálování na okamžik. Přidávají přednost horizontálnímu škálování. Horizontální navýšení kapacity se provádí horizontálně přidáním dalších počítačů (nazývaných uzly) nebo instancí aplikace do existujícího clusteru. V Kubernetes můžete ručně škálovat úpravou nastavení konfigurace pro aplikaci (například [škálování fondu uzlů](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) nebo pomocí automatického škálování.

Clustery AKS můžou automatické škálování jedním ze dvou způsobů:

Nejprve monitor [horizontálně pod automatickým škálováním](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale#autoscale-pods) sleduje požadavky na prostředky a automaticky škáluje REPLIKy pod, aby je splňovala. Když se provoz zvyšuje, automaticky se zřídí další repliky pro horizontální navýšení kapacity služeb. Podobně platí, že když se poptávka sníží, odeberou se do škálování vašich služeb. Nadefinujete metriku, na které se má škálovat, například využití procesoru. Můžete také zadat minimální a maximální počet replik, které mají být spuštěny. AKS monitoruje tuto metriku a odpovídajícím způsobem se škáluje.

V dalším kroku funkce [automatického škálování clusteru AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler) umožňuje automaticky škálovat výpočetní uzly napříč clusterem Kubernetes tak, aby splňovaly požadavky. Díky tomu můžete automaticky přidat nové virtuální počítače do základní sady škálování virtuálních počítačů Azure, když se vyžaduje větší výpočetní kapacita. Také odebere uzly, pokud již nejsou vyžadovány.

Obrázek 3-13 ukazuje vztah mezi těmito dvěma službami škálování.

![Horizontální navýšení kapacity App Serviceho plánu.](./media/aks-cluster-autoscaler.png)

**Obrázek 3-13**. Horizontální navýšení kapacity App Serviceho plánu.

Společně zajistěte, aby se zajistil optimální počet instancí kontejnerů a výpočetních uzlů pro podporu kolísání poptávky. Automatické škálování vodorovně pod optimalizuje počet požadovaných lusků. Automatické škálování clusteru optimalizuje počet požadovaných uzlů.

### <a name="scaling-azure-functions"></a>Škálování Azure Functions

Azure Functions automaticky škálovat na vyžádání. Prostředky serveru se dynamicky přiřazují a odstraňují na základě počtu aktivovaných událostí. Účtují se vám jenom výpočetní prostředky spotřebované při spuštění vašich funkcí. Fakturace vychází z počtu spuštění, času spuštění a využité paměti.

I když výchozí plán spotřeby poskytuje pro většinu aplikací ekonomické a škálovatelné řešení, možnost Premium umožňuje vývojářům pružně využít vlastní požadavky na Azure Functions. Upgrade na plán Premium poskytuje kontrolu nad velikostmi instancí, předem zaplacenými instancemi (aby se předešlo zpožděním spuštění) a vyhrazeným virtuálním počítačům.

>[!div class="step-by-step"]
>[Předchozí](deploy-containers-azure.md) 
> [Další](other-deployment-options.md)
