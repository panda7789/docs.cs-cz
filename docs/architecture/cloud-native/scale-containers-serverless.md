---
title: Škálování kontejnerů a bezserverových aplikací
description: Škálování aplikací v cloudu pomocí služby Azure Kubernetes tak, aby splňovala požadavky uživatelů díky zvýšení počtu jednotlivých prostředků počítače nebo zvýšení počtu počítačů v clusteru aplikací.
ms.date: 09/23/2019
ms.openlocfilehash: 2d0537fb3ed56beb4eccbf9b8c34a5d87793413b
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184797"
---
# <a name="scaling-containers-and-serverless-applications"></a>Škálování kontejnerů a bezserverových aplikací

Existují dva typické způsoby, jak škálovat aplikaci: horizontální navýšení kapacity a škálování. Předchozí odkazuje na přidání možností pro jednoho hostitele, zatímco druhý odkazuje na přidání do celkového počtu hostitelů. Častější způsob, jak na to uvažovat, je to, jak si sami získat a některé přátele ve městě. Pokud se jedná o jediného přítele, mohli byste se dovolat do svého pracovního automobilu na dvou sedadlech. Pokud se ale jedná o tři nebo čtyři, možná budete muset provést jednu z vašich SUVs nebo minivan, škálovat kapacitu až ke zvýšení kapacity. Když vaše celkové číslo přeskočí až do desítky nebo více, budete pravděpodobně muset převzít více vozidel (Pokud se nejedná o jinou jednotku), což demonstruje pojem horizontálního navýšení kapacity přidáním dalších instancí (v tomto případě více vozidel). Pojďme se podívat, jak to platí pro naše aplikace.

## <a name="the-simple-solution-scaling-up"></a>Jednoduché řešení: škálování

Proces upgradu stávajících serverů tak, aby jim poskytoval více prostředků (procesor, paměť, rychlost vstupu/výstupu disku, rychlost vstupu/výstupu v síti), se označuje jako horizontální *navýšení*kapacity. V cloudových nativních aplikacích se škálování většinou neodkazuje na nákup a instalaci skutečného hardwaru na fyzických počítačích, takže v seznamu dostupných možností je výběr lépe připraveného plánu. Nativní aplikace pro Cloud jsou obvykle škálovatelné změnou velikosti virtuálního počítače, která se používá k hostování jednotlivých uzlů ve fondu uzlů Kubernetes. Kubernetes koncepty, jako jsou uzly, clustery a lusky, jsou podrobněji popsány v [následující části](leverage-containers-orchestrators.md). Azure podporuje širokou škálu velikostí virtuálních počítačů, které používají [Windows](https://docs.microsoft.com/azure/virtual-machines/windows/sizes?toc=%2fazure%2fvirtual-machines%2fwindows%2ftoc.json) i [Linux](https://docs.microsoft.com/azure/virtual-machines/linux/sizes). Pokud chcete svoji aplikaci vertikálně škálovat, vytvořte nový fond uzlů s větší velikostí virtuálních počítačů uzlů a pak migrujte úlohy do nového fondu. To vyžaduje [více fondů uzlů pro cluster AKS](https://docs.microsoft.com/azure/aks/use-multiple-node-pools), což je funkce, která je aktuálně ve verzi Preview. Aplikace bez serveru se škálují až po výběru velikostí [plánů Premium](https://docs.microsoft.com/azure/azure-functions/functions-scale) a prémiových instancí nebo výběrem jiného vyhrazeného plánu služby App Service.

## <a name="scaling-out-cloud-native-apps"></a>Horizontální navýšení kapacity cloudových aplikací

Cloudové nativní aplikace podporují horizontální navýšení kapacity přidáním dalších uzlů nebo lusků k žádostem o služby. To můžete provést ručně úpravou nastavení konfigurace pro aplikaci (například [škálování fondu uzlů](https://docs.microsoft.com/azure/aks/use-multiple-node-pools#scale-a-node-pool-manually)) nebo pomocí automatického *škálování*. Automatické škálování upravuje prostředky používané aplikací, aby reagovaly na poptávku, podobně jako termostat reaguje na teplotu voláním pro další vytápění nebo chlazení. Při použití automatického škálování je ruční škálování zakázané.

Clustery AKS se můžou škálovat jedním ze dvou způsobů:

- [Automatické škálování clusteru](https://docs.microsoft.com/azure/aks/cluster-autoscaler) sleduje lusky, které není možné naplánovat na uzlech z důvodu omezení prostředků. Podle potřeby přidá další uzly.
- Horizontální navýšení **pod AutoScale** používá server metrik v clusteru Kubernetes ke sledování požadavků na prostředky v luskech. Pokud služba potřebuje víc prostředků, zvýší se počet lusků.

Obrázek 3-13 ukazuje vztah mezi těmito dvěma službami škálování.

![Horizontální navýšení kapacity App Serviceho plánu.](./media/aks-cluster-autoscaler.png)

**Obrázek 3-13**. Horizontální navýšení kapacity App Serviceho plánu.

Tyto služby mohou také snížit počet lusků nebo uzlů podle potřeby. Tyto dvě služby můžou spolupracovat společně a často se nasazují společně v clusteru. V kombinaci se horizontální automatické škálování pod ním zaměřuje na spouštění počtu lusků potřebných pro splnění požadavků aplikace. Automatické škálování clusteru se zaměřuje na spouštění počtu uzlů potřebných k podpoře naplánovaných lusků.

### <a name="scaling-azure-functions"></a>Škálování Azure Functions

Azure Functions automaticky podporuje horizontální navýšení kapacity. Výchozí plán spotřeby přidává (a odebírá) prostředky dynamicky na základě počtu triggerů přicházejících do. Účtují se vám poplatky za výpočetní prostředky, které se používají, když vaše funkce běží na základě počtu spuštění, času spuštění a využité paměti. Pomocí plánu Premium získáte stejné funkce, ale můžete také řídit velikosti instancí, které se používají, už nemusíte začínat (aby se předešlo prodlevám při spuštění), a nakonfigurovat vyhrazené virtuální počítače, na kterých se budou spouštět vaše funkce. Výchozí konfigurace by měla pro většinu aplikací poskytovat ekonomické a škálovatelné řešení. možnost Premium umožňuje vývojářům flexibilitu pro vlastní Azure Functions požadavky.

## <a name="references"></a>Reference

- [AKS více fondů uzlů](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [Automatické škálování clusteru AKS](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [Kurz: škálování aplikací v AKS](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Azure Functions škálování a hostování](https://docs.microsoft.com/azure/azure-functions/functions-scale)

>[!div class="step-by-step"]
>[Předchozí](deploy-containers-azure.md)
>[Další](other-deployment-options.md)
