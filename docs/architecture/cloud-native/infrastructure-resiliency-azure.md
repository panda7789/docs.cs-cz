---
title: Odolnost platformy Azure
description: Architekt cloudových nativních aplikací .NET pro Azure | Odolnost cloudové infrastruktury s Azure
ms.date: 06/30/2019
ms.openlocfilehash: 02d661952c860da25442b0fa9fed0d5f93abe023
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72520769"
---
# <a name="azure-platform-resiliency"></a>Odolnost platformy Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Sestavování spolehlivé aplikace v cloudu se liší od tradičního vývoje místních aplikací. I když jste si v minulosti koupili vyšší kapacitu hardwaru pro horizontální navýšení kapacity, v cloudovém prostředí, které nakonfigurujete. Místo toho, aby se zabránilo chybám, je cílem minimalizovat jejich účinky a zachovat stabilní systém.

V takovém případě spolehlivé cloudové aplikace zobrazují různé charakteristiky:

- Jsou odolné proti chybám proti problémům a fungují i nadále.
- Jsou vysoce dostupné (HA) a běží tak, jak jsou navržené v dobrém stavu bez významného výpadku.

Porozumět tomu, jak tyto charakteristiky vzájemně spolupracují a jak ovlivňují náklady – je nezbytné pro vytvoření spolehlivé cloudové nativní aplikace. Dál se podíváme na způsoby, jak můžete vytvořit odolnost a dostupnost v cloudových nativních aplikacích využívajících funkce z cloudu Azure.

## <a name="design-with-redundancy"></a>Návrh s redundancí

Selhání se liší v rozsahu dopadu. Selhání hardwaru, jako je například selhání disku, může ovlivnit jeden uzel v clusteru. Neúspěšný síťový přepínač může mít vliv na celý stojan serveru. Méně běžné chyby, jako je například výpadek napájení, můžou rušit celé datové centrum. Jenom zřídka, celá oblast bude nedostupná.

[Redundance](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy) je jedním ze způsobů, jak zajistit odolnost aplikace. Přesná úroveň redundance závisí na vašich obchodních požadavcích a ovlivní jak náklady, tak i složitost vašeho systému. Nasazení ve více oblastech je například dražší a složitější pro správu než nasazení v jedné oblasti. Budete potřebovat provozní postupy pro správu převzetí služeb při selhání a navrácení služeb po obnovení. Dodatečné náklady a složitost můžou být odůvodněné u některých obchodních scénářů a ne u jiných.

Chcete-li architekt redundanci, je třeba určit kritické cesty v aplikaci a pak zjistit, jestli je v každé pozici v cestě redundance? Pokud by se podsystém nezdařil, aplikace převezme služby něco jiného? Nakonec budete potřebovat jasné porozumění funkcím integrovaným do cloudové platformy Azure, které můžete využít ke splnění požadavků na redundanci. Tady jsou doporučení pro redundanci architektury:

- *Nasaďte více instancí služeb.* Pokud vaše aplikace závisí na jedné instanci služby, vytvoří se v jednom bodě selhání. Zřizování více instancí vylepšuje odolnost a škálovatelnost. Při hostování ve službě Azure Kubernetes můžete deklarativně nakonfigurovat redundantní instance (sady replik) v souboru manifestu Kubernetes. Hodnotu počtu replik lze spravovat programově, na portálu nebo prostřednictvím funkcí automatického škálování, které budou popsány později.

- *Využití nástroje pro vyrovnávání zatížení.* Vyrovnávání zatížení distribuuje požadavky vaší aplikace na funkční instance služby a automaticky odebere chybné instance z rotace. Při nasazování do Kubernetes je možné vyrovnávání zatížení zadat v souboru manifestu Kubernetes v části služby.

- *Plánování nasazení ve více oblastech.* Pokud je vaše aplikace nasazená v jedné oblasti a tato oblast nebude k dispozici, bude vaše aplikace také nedostupná. To může být nepřijatelné pod podmínkami smluv o úrovni služeb vaší aplikace. Místo toho zvažte nasazení aplikace a jejích služeb napříč různými oblastmi. Například cluster Azure Kubernetes Service (AKS) je nasazený do jedné oblasti. Pokud chcete systém ochránit před místním selháním, můžete nasadit aplikaci do několika clusterů AKS napříč různými oblastmi a pomocí funkce [spárované oblasti](https://buildazure.com/2017/01/06/azure-region-pairs-explained/) koordinovat aktualizace platforem a nastavit prioritu úsilí při obnovení.

- *Povolte [geografickou replikaci](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication).* Geografická replikace pro služby, jako je Azure SQL Database a Cosmos DB, vytvoří sekundární repliky vašich dat napříč několika oblastmi. I když budou obě služby automaticky replikovat data ve stejné oblasti, geografická replikace vás chrání před oblastním výpadkem tím, že vám umožní převzít služby při selhání do sekundární oblasti. Dalším osvědčeným postupem pro geografickou replikaci na středech pro ukládání imagí kontejneru. Pokud chcete nasadit službu v AKS, musíte image Uložit a načíst z úložiště. Azure Container Registry se integruje s AKS a může bezpečně ukládat image kontejnerů. Pro zlepšení výkonu a dostupnosti zvažte geografickou replikaci imagí do registru v každé oblasti, kde máte cluster AKS. Každý cluster AKS pak vyžádá image kontejneru z místního registru kontejneru ve své oblasti, jak je znázorněno na obrázku 6-6:

![Replikované prostředky napříč oblastmi](./media/replicated-resources.png)

**Obrázek 6-6**. Replikované prostředky napříč oblastmi

- *Implementujte Nástroj pro vyrovnávání zatížení provozu DNS.* [Azure Traffic Manager](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview) poskytuje vysokou dostupnost pro kritické aplikace vyrovnáváním zatížení na úrovni DNS. Může směrovat provoz do různých oblastí na základě geografické oblasti, doby odezvy clusteru a dokonce i stavu koncového bodu aplikace. Azure Traffic Manager může například směrovat zákazníky do nejbližšího clusteru AKS a instance aplikace. Pokud máte více clusterů AKS v různých oblastech, použijte Traffic Manager k řízení způsobu, jakým přenos toků do aplikací spuštěných v jednotlivých clusterech. Obrázek 6-7 ukazuje tento scénář.

![AKS a Azure Traffic Manager](./media/aks-traffic-manager.png)

**Obrázek 6-7**. AKS a Azure Traffic Manager

## <a name="design-for-scalability"></a>Návrh pro škálovatelnost

Cloud Thrives při škálování. Schopnost zvýšit nebo snížit systémové prostředky na zvýšení nebo snížení zátěže systému je klíčovým principemem cloudu Azure. Abyste ale mohli efektivně škálovat aplikaci, potřebujete pochopit funkce škálování jednotlivých služeb Azure, které zahrnete do své aplikace.  Tady jsou doporučení pro efektivní implementaci škálování v systému.

- *Návrh pro škálování.* Aplikace musí být navržena pro škálování. Aby bylo možné začít, služby by měly být bezstavové, aby bylo možné směrovat požadavky do libovolné instance. Bezstavové služby také znamená, že přidání nebo odebrání instance nemá nepříznivý vliv na aktuální uživatele.

- *Rozdělit úlohy na oddíly*. Rozkládání domén na nezávislé, samostatné mikroslužby umožňují škálovat každou službu nezávisle na ostatních. Služby obvykle budou mít různé potřeby a požadavky na škálovatelnost. Dělení vám umožní škálovat jenom to, co je potřeba škálovat, aniž byste museli škálovat celou aplikaci.

- *Upřednostnit škálování na* více instancí. Cloudové aplikace přikládají horizontální navýšení kapacity prostředků na rozdíl od škálování. Horizontální škálování (označuje se také jako horizontální škálování) zahrnuje přidání dalších prostředků služby do stávajícího systému, aby bylo možné splnit a sdílet požadovanou úroveň výkonu. Vertikální škálování (označuje se také jako vertikální škálování) zahrnuje nahrazení existujících prostředků výkonnějším hardwarem (více jader disku, paměti a zpracování). Horizontální navýšení kapacity se dá vyvolávat automaticky funkcemi automatického škálování, které jsou dostupné v některých cloudových prostředcích Azure. Horizontální navýšení kapacity mezi více prostředky také zvyšuje redundanci celého systému. Nakonec je škálování jednoho prostředku obvykle dražší než horizontální navýšení kapacity mezi mnoho menších prostředků. Obrázek 6-8 ukazuje dva přístupy:

![Horizontální navýšení kapacity oproti škálování](./media/scale-up-scale-out.png)

**Obrázek 6-8.** Horizontální navýšení kapacity oproti škálování

- *Škálujte proporcionálně.* Při škálování služby Vezměte v úvahu *sady prostředků*. Pokud byste chtěli významně škálovat konkrétní službu, což by mělo mít vliv na úložiště dat v back-endu, mezipaměti a závislé služby? Některé prostředky, jako Cosmos DB, se můžou škálovat proporcionálně, zatímco spousta dalších ne. Chcete zajistit, aby se prostředky nezměnily na místo, kde dojde k vyčerpání dalších přidružených prostředků.

- *Vyhněte se spřažení.* Osvědčeným postupem je zajistit, aby uzel nevyžadoval místní spřažení, což se často označuje jako *relace v relaci Sticky*. Požadavek by měl být schopný směrovat do jakékoli instance. Pokud potřebujete zachovat stav, měl by se Uložit do distribuované mezipaměti, jako je například [Azure Redis Cache](https://azure.microsoft.com/services/cache/).

- *Využijte výhod funkcí automatického škálování platformy.* Používejte integrované funkce automatického škálování, kdykoli je to možné, ale nemusíte používat vlastní mechanismy nebo mechanizmy třetích stran. Pokud je to možné, použijte plánovaná pravidla škálování k zajištění dostupnosti prostředků bez prodlevy při spuštění, ale podle potřeby přidejte do pravidel reaktivní automatické škálování, abyste se mohli vypořádat s neočekávanými změnami v poptávce. Další informace najdete v tématu [pokyny](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)k automatickému škálování.

- *Škálování je agresivní.* Konečným postupem by bylo horizontální navýšení kapacity, aby bylo možné rychle vyhovět okamžitým špičkám v provozu bez ztráty podnikání. A pak můžete škálovat (tj. odebrat nepotřebné instance), aby byl systém stabilní. Jednoduchým způsobem, jak to provést, je nastavit dobu chladnutí, což je čas, který se má čekat mezi operacemi škálování, na pět minut při přidávání prostředků a až 15 minut pro odebrání instancí.

## <a name="built-in-retry-in-services"></a>Integrované opakování ve službách

Doporučujeme, abyste provedli osvědčené postupy implementace programových opakovaných operací v předchozí části. Mějte na paměti, že mnoho služeb Azure a jejich odpovídajících klientských SDK zahrnuje i mechanismy opakování. Následující seznam shrnuje funkce opakování v řadě služeb Azure, které jsou popsány v této příručce:

- *Azure Cosmos DB.* Třída <xref:Microsoft.Azure.Documents.Client.DocumentClient> z rozhraní API klienta automaticky odřadí neúspěšné pokusy. Počet opakovaných pokusů a maximální doba čekání je konfigurovatelná. Výjimky vyvolané klientským rozhraním API jsou požadavky, které překračují zásady opakování nebo nepřechodné chyby.

- *Azure Redis Cache.* Klient Redis StackExchange používá třídu Správce připojení, která zahrnuje opakování při neúspěšných pokusech. Počet opakovaných pokusů, konkrétní zásady opakování a doba čekání jsou konfigurovatelné.

- *Azure Service Bus.* Klient Service Bus zpřístupňuje [třídu RetryPolicy](xref:Microsoft.ServiceBus.RetryPolicy) , která se dá nakonfigurovat s Back-off intervalem, počtem opakování a <xref:Microsoft.ServiceBus.RetryExponential.TerminationTimeBuffer>, která určuje maximální dobu, kterou může operace trvat. Výchozí zásada má devět maximálních pokusů o opakování s omezení rychlosti obdobím 30 sekund mezi pokusy.

- *Azure SQL Database.* Při použití knihovny [Entity Framework Core](https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency) je k dispozici podpora opakování.

- *Azure Storage.* Klientská knihovna pro úložiště podporuje operace opakování. Strategie se liší napříč tabulkami, objekty BLOB a frontami služby Azure Storage. I když je funkce geografické redundance povolená, alternativní pokusy se přepínají mezi primárními a sekundárními umístěními služby úložiště.

- *Event Hubs Azure.* Klientská knihovna pro centrum událostí obsahuje vlastnost RetryPolicy, která zahrnuje konfigurovatelnou omezení rychlosti funkci exponenciálního typu.

>[!div class="step-by-step"]
>[Předchozí](application-resiliency-patterns.md)
>[Další](resilient-communications.md)
